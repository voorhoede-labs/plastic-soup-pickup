<template>
  <div class="">
    <nav>
      <button @click="activeTab = 'leaderboard'" :class="{'is-active': activeTab === 'leaderboard'}">
        Leaderboard
      </button>
      <button @click="activeTab = 'challenges'" :class="{'is-active': activeTab === 'challenges'}">
        Challenges
      </button>
    </nav>
    <section v-if="activeTab === 'leaderboard'">
      <h4>Leaderboard</h4>
    </section>
    <section v-if="activeTab === 'challenges'">
      <ul class="challenge-badges">
        <ChallengeBadge
          image="dummy.jpg"
          title="Getting Started"
          points="25"
        />
        <ChallengeBadge
          image="dummy.jpg"
          title="Collector"
          points="50"
        />
        <ChallengeBadge
          image="dummy.jpg"
          title="Litter Selfie"
          points="50"
        />
        <ChallengeBadge
          image="dummy.jpg"
          title="Picking Spree"
          points="50"
        />
        <ChallengeBadge
          image="dummy.jpg"
          title="Power Up!"
          points="100"
        />
        <ChallengeBadge
          image="dummy.jpg"
          title="Pick Up 10"
          points="250"
        />
      </ul>
      <a href="/photo">let's pickup plastic!</a>
    </section>
  </div>
</template>



<script>
  import ChallengeBadge from '~/components/ChallengeBadge.vue'

  export default {
    components: {
      ChallengeBadge
    },
    data: function () {
      return {
        activeTab: 'challenges',
      }
    }
  }
</script>

<style>
  .challenge-badges {
    display: flex;
    flex-wrap: wrap;
  }

  .challenge-badges li {
    width: 50%;
  }

  .challenge-badges figcaption {
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
</style>
