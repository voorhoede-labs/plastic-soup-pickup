<template>
  <a :href="url" class="share-twitter">Share on Twitter</a>
</template>

<style>
  .share-twitter {
    margin: 1em 0;
  }
</style>

<script>
  export default {
    data () {
      const baseUrl = 'https://twitter.com/share?url='
      const docUrl = process.browser ? document.URL : ''
      return { url: baseUrl + docUrl }
    }
  }
</script>
