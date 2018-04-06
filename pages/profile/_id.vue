<template>
  <div class="profile">
    <h1 class="profile__title" v-if="user">{{ user.username }}</h1>
    <img v-if="avatar" class="profile__image" :src="avatar.src" role="presentation" />
    <img v-else class="profile__image profile__image--empty" src="~/assets/svgs/icon-profile.svg" role="presentation" />
    <ul class="profile__tabs">
      <li><button :class="{'profile__tab--active': activeTab === 'challenge'}" class="profile__tab profile__tab--first" @click="setActiveTab('challenge')">Challenge</button></li>
      <li><button :class="{'profile__tab--active': activeTab === 'leaderboard'}" class="profile__tab profile__tab--last" @click="setActiveTab('leaderboard')">Leaderboard</button></li>
    </ul>
    <div v-if="activeTab === 'challenge'">
      <p>Heth</p>
    </div>
    <div v-if="activeTab === 'leaderboard'">
      <p>hetheht</p>
    </div>
  </div>
</template>

<style>
  .profile {
    padding: 32px 16px;
    background: #F1F1F1;
    min-height: 100vh;
  }

  .profile__title {
    text-align: center;
    font-size: 1.5rem;
    color: #2B2F47;
    margin-bottom: 32px;
  }

  .profile__image {
    display: block;
    width: 150px;
    height: 150px;
    margin: 0 auto;
    background-color: #DEDEDE;
    border-radius: 100%;
    border: 1px solid #D7D7D7;
    object-fit: cover;
    margin-bottom: 32px;
  }

  .profile__image--empty {
    object-fit: none;
  }

  .profile__tabs {
    text-align: center;
  }

  .profile__tabs li {
    display: inline-block;
  }

  .profile__tab {
    display: inline-block;
    color: #2B2F47;
    border-radius: 0;
    font-weight: bold;
    border: 0;
    background: white;
  }

  .profile__tab--active {
    color: white;
    background: #F26F69;
  }

  .profile__tab--first {
    border-top-left-radius: 16px;
    border-bottom-left-radius: 16px;
  }

  .profile__tab--last {
    border-top-right-radius: 16px;
    border-bottom-right-radius: 16px;
  }
</style>

<script>
  import axios from 'axios'
  function request (url) {
    return axios.get(url).then(response => response.data)
  }

  export default {
    validate({ params }) {
      return !isNaN(+params.id)
    },
    created() {
      let id = this.getCookie('psp-user-id')

      if (!id) {
        id = this.setCookie('psp-user-id', new Date().getTime(), 999)
      }

      this.cookieId = id
    },
    data() {
      return {
        cookieId: null,
        activeTab: 'challenge'
      }
    },
    async asyncData({ params }) {
      const username = 'aapje'
      const [user, avatar] = await Promise.all([
        request(`https://pick-up-10-api-csyeqvdphz.now.sh/api/users/${username}/`),
        request(`https://pick-up-10-api-csyeqvdphz.now.sh/api/users/${username}/avatar`)
      ])

      return { avatar, user }
    },
    computed: {
      itsMe: function() {
        return this.userId === this.cookieId
      }
    },
    methods: {
      setActiveTab: function(name) {
        this.activeTab = name
      },
      setCookie(name, value, days) {
        if (!process.browser) {
          return
        }

        let expires;
        if (days) {
          let date = new Date()
          date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000))
          expires = '; expires=' + date.toGMTString()
        }
        else {
          expires = ''
        }

        document.cookie = name + '=' + value + expires + '; path=/'
        return value
      },
      getCookie(name) {
        if (!process.browser) {
          return ''
        }

        if (document.cookie.length > 0) {
          let c_start = document.cookie.indexOf(name + '=')
          if (c_start != -1) {
            c_start = c_start + name.length + 1
            let c_end = document.cookie.indexOf(';', c_start)
            if (c_end == -1) {
              c_end = document.cookie.length
            }
            return unescape(document.cookie.substring(c_start, c_end))
          }
        }
        return ''
      }
    }
  }
</script>
