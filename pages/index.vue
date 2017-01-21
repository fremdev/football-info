<template>
  <section class="container">
    <h1>
      Full list of competitions:
    </h1>
    <ul>
      <li v-for="league in leagues">
        {{ league.caption }}
      </li>
    </ul>
  </section>
</template>

<script>
import axios from 'axios'

export default {
  async data (context) {
    const { data } = await axios.get('http://api.football-data.org/v1/competitions')
    return { leagues: data }
  }
}
</script>

<style scoped>
</style>
