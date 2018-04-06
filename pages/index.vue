<template>
  <div>
    <section class="container">
      <div>
        <app-intro-video/>
        <a href="/challenge" class="button">
          let's go!
        </a>
        <introduction/>
        <blockquote>I'm an awesome quote</blockquote>
      </div>
    </section>
    <share-on-facebook/>
    <share-on-twitter/>
    <app-footer/>
  </div>
</template>

<script>
import AppIntroVideo from '~/components/AppIntroVideo.vue'
import Introduction from '~/components/Introduction.vue'
import AppFooter from '~/components/AppFooter.vue'
import ShareOnFacebook from '~/components/ShareOnFacebook.vue'
import ShareOnTwitter from '~/components/ShareOnTwitter.vue'

export default {
  components: {
    AppIntroVideo,
    Introduction,
    AppFooter,
    ShareOnFacebook,
    ShareOnTwitter,
  }
}
</script>

