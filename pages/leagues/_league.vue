<template>
  <div>
    <h3>{{ leagueTable.leagueCaption }}</h3>
    <h5>{{ leagueTable.matchday }}</h5>
    <table>
      <tbody>
        <tr v-for="team in leagueTable.standing">
          <td>{{ team.position }}</td>
          <td>{{ team.teamName }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'
import config, { leagueIds } from '~/config/'
const leagueIndexes = ['']
export default {
  name: 'league',
  validate({ params }) {
    return leagueIds[params.league];
  },
  async data (context) {
    const id = leagueIds[context.params.league];
    const reqConfig = { headers: {"X-Auth-Token": config.apiKey} };
    const { data } = await axios.get(`http://api.football-data.org/v1/competitions/${id}/leagueTable`, reqConfig)
    return { leagueTable: data }
  }
}
</script>

<style scoped>
</style>
