<template>
  <div class="container">
    <h1>{{ msg }}</h1>
    <div>
      <div v-for="article in news" :key="article.dataSourceIdentifier">
        <img :src="article.images[0].url" alt="article image">
        <h2><a :href="article.links.web.href">{{ article.headline }}</a></h2>
        <p>{{ article.published }}</p>
        <p>{{ article.byline }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  props: {
    msg: String
  },
  data() {
    return {
      news: null
    }
  },
  created() {
    const url = 'http://site.api.espn.com/apis/site/v2/sports/football/nfl/news'

    fetch(url)
      .then(response => response.json())
      .then(data => {
        this.news = data.articles
      })
      .catch(err => {
        console.log(err.message || err);
        this.news = false
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.container {
  border: 1px solid red;
}
</style>
