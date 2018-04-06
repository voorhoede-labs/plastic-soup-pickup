<template>
  <div class="photo-preview">
    <div class="photo-preview__loader-wrapper" v-if="loading">
      <div class="photo-preview__loader"/>
    </div>
    <template v-else>
      <h2 class="photo-preview__title">{{ title }}</h2>
      <ul class="photo-preview__tags">
        <li v-for="tag in tags" class="photo-preview__tag" :key="tag">{{ tag }}</li>
      </ul>
    </template>
    <img class="photo-preview__image" :src="src"/>
  </div>
</template>

<script>

export default {
  props: {
    src: String,
    title: String,
    tags: {
      required: false,
      type: Array,
    },
    loading: Boolean,
  }
}
</script>

<style>
.photo-preview {
  margin: .5rem;
  position: relative;
  background: #2B2F47;
}

.photo-preview > * {
  z-index: 1;
}

.photo-preview__title {
  position: absolute;
  top: 1rem;
  left: 1rem;

  color: #f1f1f1;
  font-family: 'proxima nova';
  font-weight: normal;
  text-transform: uppercase;
}

.photo-preview__image {
  opacity: .5;
  width: 100%;
  z-index: 0;
  position: relative;
}

.photo-preview__tags {
  color: #f1f1f1;
  list-style-type: none;
  position: absolute;
  bottom: 0;
  left: 0;
  width: 80%;
}

.photo-preview__tag {
  padding: .125rem .325rem;
  display: inline-block;
  background: #F26F69;
  border-radius: .5rem;
  text-transform: uppercase;
  margin-left: .5rem;
  margin-bottom: .5rem;
}

.photo-preview__loader-wrapper {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.photo-preview__loader {
  display: inline-block;
  width: 4rem;
  height: 4rem;
  border: .5rem solid #f1f1f1;;
  border-top: .5rem solid #f26f69;
  animation: rotate 1.1s cubic-bezier(0.71, 0.32, 0.26, 0.67) infinite;
  border-radius: 50%;
}

@keyframes rotate {
  to {
    transform: rotate(1turn);
  }
}
</style>
