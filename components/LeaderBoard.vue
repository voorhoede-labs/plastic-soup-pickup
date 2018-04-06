<template>
  <div>
    <h4>Leaderboard</h4>
    <ol>
      <li v-for="user in sortedUsers" :key="user.id">
        <span class="username">
          {{ user.id }}
        </span>
        <span class="points">
          {{ user.numImages * 13 }}
        </span>
      </li>
    </ol>
  </div>
</template>

<style>
  li {
    display: flex;
    justify-content: space-between;
    font-size: 1.25em;
    border-bottom: 1px solid black;
    padding: 0.25em;
  }

  .points {
    display: flex;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    background: red;
    border-radius: 50%;
    text-align: center;
    width: 2rem;
    height: 2rem;
    color: white;
    font-weight: bold;
  }
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
