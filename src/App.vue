<template>

  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-12">

        <img alt="Vue logo" src="./assets/logo.png">
        </div>
        <div class="col-12 mt-5">

        <SearchDomain msg="Server Diagnostician"/>
        </div>

      </div>
    </div>

  </div>
</template>

<script>
import SearchDomain from './components/SearchDomain.vue'

export default {
  name: 'App',
  components: {
    SearchDomain
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #4f5255;
  margin-top: 60px;
}
</style>
