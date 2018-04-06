<template>
  <div>
    <app-intro-video/>
    <introduction/>
    <footer/>
  </div>
</template>

<script>
import AppIntroVideo from '~/components/AppIntroVideo.vue'
import Introduction from '~/components/Introduction.vue'
import Footer from '~/components/Footer.vue'

export default {
  created() {
    const userId = this.getCookie('psp-user-id')

    if (userId) {
      this.userId = userId
    } else {
      this.setCookie('psp-user-id', new Date().getTime(), 999)
    }
  },
  components: {
    AppIntroVideo,
    Introduction,
    Footer,
  },
  data () {
    return {
      userId: null
    }
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

