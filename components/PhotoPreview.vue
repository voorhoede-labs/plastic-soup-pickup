<template>
  <div class="photo-preview">
    <img :src="src" class="image-preview"/>
  </div>
</template>

<script>
export default {
  props: {
    src: String,
    entities: {
      required: false,
      type: Array,
    },
    bestGuess: {
      required: false,
      type: Object,
    },
  }
}
</script>
