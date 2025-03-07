<template>
    <div class="news-container">
        <NewsComp />
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
</style>