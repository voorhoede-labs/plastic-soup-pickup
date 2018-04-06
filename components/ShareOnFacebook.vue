<template>
  <a :href="url" class="share-fb">Share on Facebook</a>
</template>

<style>
  .share-fb {
    margin: 1em 0;
  }
</style>

<script>
  export default {
    data () {
      const baseUrl = 'https://www.facebook.com/sharer/sharer.php?u='
      const docUrl = process.browser ? document.URL : ''
      return { url: baseUrl + docUrl }
    }
  }
</script>


