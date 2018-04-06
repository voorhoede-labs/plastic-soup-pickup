<template>
  <div>
    <app-intro-video/>
    <introduction/>
    <app-impact/>
    <app-footer/>
  </div>
</template>

<script>
import AppIntroVideo from '~/components/AppIntroVideo.vue'
import Introduction from '~/components/Introduction.vue'
import AppImpact from '~/components/AppImpact.vue'
import AppFooter from '~/components/AppFooter.vue'

export default {
  created() {
    let id = this.getCookie('psp-user-id')

    if (!id) {
      id = this.setCookie('psp-user-id', new Date().getTime(), 999)
    }

    this.userId = id
  },
  components: {
    AppIntroVideo,
    Introduction,
    AppFooter,
    AppImpact
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

