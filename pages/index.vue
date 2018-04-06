<template>
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
</template>

<script>
import AppIntroVideo from '~/components/AppIntroVideo.vue'
import Introduction from '~/components/Introduction.vue'

export default {
  components: {
    AppIntroVideo,
    Introduction
  }
}
</script>

