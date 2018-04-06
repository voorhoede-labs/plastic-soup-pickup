<template>
  <li>
    <figure class="challenge-badge" :class="{'is-active': isActive}">
      <img
        v-bind:src="require(`~/assets/challenge-badges/${image}`)"
        alt=""
        width="150px"
        height="150px"
      >
      <figcaption>{{ title }}</figcaption>
      <p>{{ points }} points</p>
    </figure>
  </li>
</template>

<style>
  .challenge-badge {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .challenge-badge.is-active {
    color: green;
  }
</style>

<script>
export default {
  data: ({ title }) => {
    return { isActive: process.browser && localStorage.getItem(title) ? true : false }
  },
  props: {
    image: String,
    title: String,
    points: String,
  }
}
</script>
