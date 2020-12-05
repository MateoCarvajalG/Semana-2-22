<template>
  <div id="app">
    <ApiWeather></ApiWeather>
  </div>
</template>

<script>
import ApiWeather from './components/ApiWeather.vue'


export default {
  name: 'App',
  components: {
    ApiWeather,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


