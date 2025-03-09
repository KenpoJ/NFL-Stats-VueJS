<template>
  <div class="container-home">
    <div class="news-container">
        <NewsComp />
    </div>
  </div>
  <div class="container">
    <div class="column">
        column one
    </div>
    <div class="column">
        column two
    </div>
    <div class="column">
        column three
    </div>
  </div>
</template>

<script>
import NewsComp from './components/NewsComp.vue'

export default {
  name: 'HomePage',
  components: {
    NewsComp
  },
  props: {
    msg: String
  },
}
</script>

<style lang="scss">
.content {
  .container {
    display: grid;
    grid-template-columns: 33% 33% 33%;
    grid-template-rows: min-content 1fr;
    gap: 20px;
    overflow: scroll;

    .news-container {
      grid-column-start: 1;
      grid-column-end: span 3;
    }
  }
}
.container-news {
  overflow: scroll;
}
</style>