<template>
  <section class="container">
    <div>
      <app-intro-video/>
      <a href="/challenge" class="button">
        let's go!
      </a>
      <blockquote>I'm an awesome quote</blockquote>
    </div>
  </section>
</template>

<script>
import AppIntroVideo from '~/components/AppIntroVideo.vue'

export default {
  components: {
    AppIntroVideo
  }
}
</script>

