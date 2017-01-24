<template>
  <section class="container">
    <h1>
      Choose a competition:
    </h1>
    <div class="leagues">
      <div class="league">
        <nuxt-link to="/leagues/premier/">Premier League</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/championship/">Championship</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/bundesliga/">1. Bundesliga</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/bundesliga-2/">2. Bundesliga</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/eredivisie/">Eredivisie</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/league-1/">Ligue 1</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/league-2/">Ligue 2</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/primera/">Primera Division</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/segunda/">Liga Adelante</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/serie-a/">Serie A</nuxt-link>
      </div>
      <div class="league">
        <nuxt-link to="/leagues/primeira/">Primeira Liga</nuxt-link>
      </div>
    </div>
  </section>
</template>

<style scoped>
.league {
  padding-bottom: 10px;
}
a {
  text-decoration: none;
  padding: 3px;
}
a:hover {
  background-color: #5fa292;
  color: #fff;
}
</style>
