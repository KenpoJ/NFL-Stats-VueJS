<template>
  <div class="container">
    <ul>
      <li><a href="#/">Home</a></li>
      <li><a href="#/scores">Scores</a></li>
      <li><a href="#/teams">Teams</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'MainNav',
  props: {
    // msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
ul {
  display: flex;
  gap: 10px;
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;

  li {
    a {
      display: block;
      padding: 10px;
      text-decoration: none;
      color: #333;
      font-weight: bold;
      &:hover {
        background-color: #f1f1f1;
      }
    }
  }
}
</style>
