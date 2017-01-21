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
const leagueIds = {
  'premier': 426,
  'championship': 427,
  'bundesliga': 430,
  'bundesliga-2': 431,
  'eredivisie': 433,
  'league-1': 434,
  'league-2': 435,
  'primera': 436,
  'segunda': 437,
  'serie-a': 438,
  'primeira': 439,
};
import axios from 'axios'
const leagueIndexes = ['']
export default {
  name: 'league',
  validate({ params }) {
    return leagueIds[params.league];
  },
  async data (context) {
    const id = leagueIds[context.params.league];
    const { data } = await axios.get(`http://api.football-data.org/v1/competitions/${id}/leagueTable`)
    return { leagueTable: data }
  }
}
</script>

<style scoped>
</style>
