<template>
  <section class="container">
    <h3>{{ leagueTable.leagueCaption }}</h3>
    <h5>Current positions before matchday {{ leagueTable.matchday }}</h5>
    <table class="league">
      <tbody>
        <tr v-for="team in leagueTable.standing">
          <td class="league__position">{{ team.position }}</td>
          <td><span class="team"><span class="team__logo" :style="{backgroundImage: `url(${team.crestURI})`}"></span><span class="team__name">{{ team.teamName }}</span></span></td>
        </tr>
      </tbody>
    </table>
  </section>
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
.league {
  margin: 0 auto;
  text-align: left;
  vertical-align: middle;
}
.league__position {
  text-align: right;
  padding-right: 5px;
}
.team__logo {
  display: inline-block;
  background-size: contain;
  width: 30px;
  height: 30px;
  background-repeat: no-repeat;
  background-position: center top;
  vertical-align: top;
  margin-right: 7px;
}
.team {
  vertical-align: middle;
}
.team__name {
  line-height: 30px;
}
</style>
