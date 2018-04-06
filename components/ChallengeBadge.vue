<template>
  <li>
    <figure class="challenge-badge">
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
</style>

<script>
export default {
  props: {
    image: String,
    title: String,
    points: String,
  }
}
</script>
