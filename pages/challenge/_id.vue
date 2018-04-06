<template>
  <div>
    <router-link to="/challenge">Back</router-link>
    <figure>
      <img
        src="~/assets/challenge-badges/team-up.png"
        alt=""
        width="150px"
        height="150px"
      >
      <figcaption>{{ challenge.title }}</figcaption>
      <p>{{ challenge.points }} points</p>
    </figure>
  </div>
</template>

<script>
  import challenges from '~/stubs/challenges.json';

  export default {
    data() {
        return {
          challenge: challenges.find(challenge => challenge.slug === this.$route.params.id)
        }
    }
  }
</script>
