<template>
  <div>
    <h4>Leaderboard</h4>
    <ol>
      <li v-for="user in sortedUsers" :key="user.id">
        {{ user.id }} has {{ user.numImages }} point{{ user.numImages === 1 ? '' : 's' }}!!!
      </li>
    </ol>
  </div>
</template>

<style>
</style>

<script>
import json from '../stubs/users.json'

export default {
  data() {
    return {
      users: []
    }
  },
  props: {

  },
  computed: {
    sortedUsers() {
      return this.users.slice().sort(function(winner, loser) {
        return Object.keys(winner.images).length < Object.keys(loser.images).length // smaller than looks strange, but it's sort descending
      })
    }
  },
  created() {
    // fetch('/firebase').then(response => {
    //   this.users = response
    // })
    this.users = Object.keys(json.users).map(key => {
      const user = json.users[key]
      user.id = key
      user.numImages = Object.keys(user.images).length
      return user
    })
  }

}
</script>
