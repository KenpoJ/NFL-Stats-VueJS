<template>
  <div class="container-news">
    <h1 class="heading-news">{{ msg }}</h1>
    <div class="inner-container">
      <div class="article" v-for="article in news" :key="article.dataSourceIdentifier">
        <img :src="article.images[0].url" alt="article image">
        <div class="article-content">
          <h2><a :href="article.links.web.href" target="_blank">{{ article.headline }}</a></h2>
          <p>{{ article.published }}</p>
          <p>{{ article.byline }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewsComp',
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
.inner-container {
  width: 100%;
  display: flex;
  gap: 10px;
}
.heading-news {
  margin: 0;
  text-align: center;
}
.article {
  flex: 1 0 25%;
  display: flex;
  flex-direction: column;
  border: 1px solid black;
  border-radius: 5px;

  img {
    width: 100%;
    border-radius: 5px;
  }
  .article-content {
    padding: 10px;
    h2 {
      font-size: 1rem;
      margin: 0;
    }
    p {
      margin: 0;
    }
  }
}
</style>
