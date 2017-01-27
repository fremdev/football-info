<template>
  <section class="container">
    <h3>{{ leagueTable.leagueCaption }}</h3>
    <h5>Current positions before matchday {{ leagueTable.matchday }}</h5>
    <table class="league">
      <tbody>
        <tr v-for="team in leagueTable.standing">
          <td class="team__position">{{ team.position }}</td>
          <td class="team"><span class="team__wrapper"><span class="team__logo" :style="{backgroundImage: `url(${team.crestURI})`}"></span><span class="team__name">{{ team.teamName }}</span></span></td>
          <td>{{ team.playedGames }}</td>
          <td>{{ team.wins }}</td>
          <td>{{ team.draws }}</td>
          <td>{{ team.losses}}</td>
          <td>{{ team.goals}}</td>
          <td>{{ team.goalsAgainst}}</td>
          <td>{{ team.goalDifference }}</td>
          <td class="team__points">{{ team.points }}</td>
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
  text-align: right;
  vertical-align: middle;
  line-height: 1.5;
  background: #f6f6f6;
}
.team__position {
  padding-right: 5px;
}
.team__logo {
  display: inline-block;
  background-size: contain;
  width: 30px;
  height: 30px;
  background-repeat: no-repeat;
  background-position: center top;
  vertical-align: middle;
  margin-right: 7px;
}
.team {
  text-align: left;
}
.team__wrapper {
  vertical-align: middle;
}
.team__name {
  line-height: 30px;
}
.league td {
  padding: 7px 10px;
}
.league tr:nth-child(odd)>td {
    background-color: #ececec;
}
.team__points {
  font-weight: bold;
}
</style>
