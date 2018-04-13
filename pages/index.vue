<template>
  <div>
    <section class="container">
        <app-step-one/>
        <app-step-two/>
        <app-step-three/>
        <app-step-four/>
    </section>
    <app-intro-video/>
    <app-footer/>
  </div>
</template>

<script>
import AppStepOne from '~/components/AppStepOne.vue'
import AppStepTwo from '~/components/AppStepTwo.vue'
import AppStepThree from '~/components/AppStepThree.vue'
import AppStepFour from '~/components/AppStepFour.vue'
import Introduction from '~/components/Introduction.vue'
import AppFooter from '~/components/AppFooter.vue'
import ShareOnFacebook from '~/components/ShareOnFacebook.vue'
import ShareOnTwitter from '~/components/ShareOnTwitter.vue'

export default {
  created() {
    let id = this.getCookie('psp-user-id')

    if (!id) {
      id = this.setCookie('psp-user-id', new Date().getTime(), 31557600)
    }

    this.userId = id
  },
  components: {
    AppStepOne,
    AppStepTwo,
    AppStepFour,
    AppStepThree,
    Introduction,
    AppFooter,
    ShareOnFacebook,
    ShareOnTwitter
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

