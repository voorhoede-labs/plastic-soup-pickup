<template>
  <figure :class="{'is-active': isActive}">
    <router-link :to="`/challenge/${slug}`">
      <img
        v-bind:src="require(`~/assets/challenge-badges/${image}`)"
        alt=""
        width="150px"
        height="150px"
      >
    </router-link>
    <figcaption>{{ title }}</figcaption>
    <p>{{ points }} points</p>
  </figure>
</template>

<style scoped>
  figure {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin-bottom: 1rem;
  }

  figure.is-active {
    color: green;
  }

  figcaption {
    font-weight: bold;
  }
</style>

<script>
export default {
  data: ({ title }) => ({
    isActive: process.browser && localStorage.getItem(title) ? true : false
  }),
  props: {
    slug: String,
    image: String,
    title: String,
    points: String,
  }
}
</script>
