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
  components: {
    AppIntroVideo,
    Introduction,
    Footer,
  }
}
</script>

