<template>
  <footer class="app-footer">
    <engage-button />
  </footer>
</template>

<style>
  .app-footer {
    width: 100%;
    padding: 2em 0;
    margin: 0 auto;
  }
</style>

<script>
import EngageButton from '~/components/EngageButton.vue'

export default {
  components: {
    EngageButton,
  }
}
</script>

