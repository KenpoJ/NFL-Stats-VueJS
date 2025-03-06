<template>
  <div class="container">
    <div>
      <h1>{{ msg }}</h1>
      <div class="article" v-for="article in news" :key="article.dataSourceIdentifier">
        <img :src="article.images[0].url" alt="article image">
        <div class="article-content">
          <h2><a :href="article.links.web.href">{{ article.headline }}</a></h2>
          <p>{{ article.published }}</p>
          <p>{{ article.byline }}</p>
        </div>
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
<style lang="scss">
.content {
  .container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    grid-gap: 20px;
  }
  .article {
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 1px solid black;
    border-radius: 5px;

    img {
      width: 100%;
      border-radius: 5px;
    }
    .article-content {
      padding: 10px;
      h2 {
        font-size: 1.5rem;
        margin: 0;
      }
      p {
        margin: 0;
      }
    }
  }
}
</style>
