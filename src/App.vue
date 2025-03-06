<template>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />

  <div class="body">
    <div class="header">
      <MainNav/>
    </div>
    <div class="content">
      <HomePage msg="NFL News"/>
    </div>
    <div class="footer">
      <p>Footer</p>
    </div>
  </div>
</template>

<script>
import MainNav from './components/MainNav.vue'
// import HelloWorld from './components/HelloWorld.vue'
import HomePage from './components/HomePage.vue'

export default {
  name: 'App',
  components: {
    MainNav,
    HomePage
  }
}
</script>

<style>

</style>
