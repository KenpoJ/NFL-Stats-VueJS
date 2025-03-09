<template>
  <div class="container-teams">
    <div v-for="team in teams" 
    :key="team.team.id"
    class="team-card" :class="team.team.abbreviation" 
    >
        <div class="team-logo">
            <img :src="team.team.logos[1].href" alt="{{ team.team.displayName }} logo">
        </div>
        <div class="team-info">
            <h2>{{ team.team.displayName }}</h2>
            <p>{{ team.team.abbreviation }}</p>
            <p>{{ team.team.location }}</p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TeamsPage',
  props: {
    msg: String
  },
  data() {
    return {
      teams: null
    }
  },
  created() {
    const url = 'https://site.api.espn.com/apis/site/v2/sports/football/nfl/teams?limit=32'

    fetch(url)
      .then(response => response.json())
      .then(data => {
        console.log(data)
        this.teams = data.sports[0].leagues[0].teams
      })
      .catch(err => {
        console.log(err.message || err);
        this.teams = false
      })
  }
}
</script>

<style lang="scss" scoped>
.container-teams {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.team-card {
  margin-bottom: 1rem;
  flex: 0 1 48%;
  display: flex;
  align-items: center;
  border: 1px solid black;
  border-radius: 5px;

    .team-logo {
        flex: 0 1 25%;
        padding: 10px;
        img {
            width: 120px;
            height: auto;
        }
    }
}
.ARI {
    background-color: $ARI-primary;
    color: $light;
    h2 {
        color: $ARI-accent;
    }
}
</style>