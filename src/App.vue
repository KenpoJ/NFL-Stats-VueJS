<template>
  <div id="app">
    <MainNav />
    <div class="content">
      <div class="container">
        <component :is="currentView" />
      </div>
    </div>
  </div>
</template>

<script>
import { ref, computed, defineAsyncComponent } from 'vue'
import MainNav from './components/MainNav.vue'

export default {
  name: 'App',
  components: {
    MainNav
  },
  setup() {
    const routes = {
      '/': defineAsyncComponent(() => import('./HomePage.vue')),
      '/scores': defineAsyncComponent(() => import('./ScoresPage.vue')),
      '/teams': defineAsyncComponent(() => import('./TeamsPage.vue')),
      '/404': defineAsyncComponent(() => import('./NotFound.vue'))
    }

    const currentPath = ref(window.location.hash || '/')

    window.addEventListener('hashchange', () => {
      currentPath.value = window.location.hash || '/'
    })

    const currentView = computed(() => {
      return routes[currentPath.value.slice(1)] || routes['/404']
    })

    return {
      currentView
    }
  }
}
</script>

<style lang="scss">

</style>