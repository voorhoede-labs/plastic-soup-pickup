<template>
  <div>
    <h1>Leaderboard</h1>
    <div v-if="userExists">
      <ol v-if="sortedUsers.length">
        <li v-for="user in sortedUsers" :key="user.id">
          <span class="username">
            {{ user.id }}
          </span>
          <span class="points">
            {{ user.numImages * 13 }}
          </span>
        </li>
      </ol>
      <ol v-if="!sortedUsers.length">
        <li><marquee>LOADING DATA 0x000COFFEE10101ZEROONE!</marquee></li>
      </ol>
    </div>
    <div v-if="!userExists">
      <h3>HEY BUDDY</h3>
      <p>You don’t have a user name yet, mr <code>{{ userName }}</code>!!</p>
      <form method="post" action="https://pick-up-10-api-isrgvzstxl.now.sh/api/user">
        <input class="field" type="text" placeholder="Your name here!">
        <br>
        <button>Say my name</button>
      </form>
    </div>
  </div>
</template>

<style>
  li {
    display: flex;
    justify-content: space-between;
    font-size: 1.25em;
    border-bottom: 1px solid black;
    padding: 0.25em;
  }

  form {
    margin-top: 3rem;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .points {
    display: flex;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    background: red;
    border-radius: 0.5em;
    text-align: center;
    min-width: 4rem;
    height: 2rem;
    color: white;
    font-weight: bold;
  }

  .field {
    padding: 0.5rem;
    font-size: 1.25em;
  }
</style>

<script>
import json from '../stubs/users.json'

export default {
  data() {
    return {
      users: []
    }
  },
  props: {
  },
  computed: {
    sortedUsers() {
      return this.users.slice().sort(function(winner, loser) {
        return Object.keys(winner.images).length < Object.keys(loser.images).length // smaller than looks strange, but it's sort descending
      })
    },
    userExists() {
      return !!this.getCookie('psp-user-name')
    },
    userName() {
      return this.getCookie('psp-user-name') || this.getCookie('psp-user-id') || 'UNKNOWN USER ERROR'
    }
  },
  created() {
    fetch(`https://pick-up-10-api-isrgvzstxl.now.sh/api/leaderboard`).then(response => {
      if (response.ok) {
        return response.json()
      } else {
        alert('API broke :(')
      }
    }).then(users => {
      this.users = Object.keys(users).map(key => {
        const user = users[key]
        user.id = key
        user.numImages = Object.keys(user.images).length
        return user
      })
    }).catch(err => {
      console.log(err)
    })
  },
  methods: {
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
