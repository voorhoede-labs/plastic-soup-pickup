<template>
  <div>
    <nav>
      <button @click="activeTab = 'leaderboard'" :class="{'is-active': activeTab === 'leaderboard'}">
        Leaderboard
      </button>
      <button @click="activeTab = 'challenges'" :class="{'is-active': activeTab === 'challenges'}">
        Challenges
      </button>
    </nav>
    <section v-if="activeTab === 'leaderboard'">
      <LeaderBoard />
    </section>
    <section v-if="activeTab === 'challenges'">
      <ul>
        <li v-for="challenge in challenges" :key="challenge.title">
          <ChallengeBadge
            :image="challenge.image"
            :title="challenge.title"
            :points="challenge.points"
          />
        </li>
      </ul>
      <a href="/photo">let's pickup plastic!</a>
    </section>
  </div>
</template>

<script>
  import ChallengeBadge from '~/components/ChallengeBadge.vue'
  import LeaderBoard from '~/components/LeaderBoard.vue'
  import challenges from '~/stubs/challenges.json'

  export default {
    components: {
      ChallengeBadge,
      LeaderBoard
    },
    data: function () {
      return {
        activeTab: 'challenges',
        challenges,
      }
    }
  }
</script>

<style scoped>
  nav button {

  }

  ul {
    display: flex;
    flex-wrap: wrap;
  }

  ul li {
    width: 50%;
  }

  ul figcaption {
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
</style>
