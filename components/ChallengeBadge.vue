<template>
  <li>
    <figure class="challenge-badge">
      <img
      v-bind:src="require(`~/assets/challenge-badges/${image}`)"
      alt=""
      width="150px"
      height="150px"
      >
      <figcaption>Getting started</figcaption>
      <p>25 points</p>
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
    image: String
  }
}
</script>
