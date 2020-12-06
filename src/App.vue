<template>
  <div id="app">

   <encabezado-banner></encabezado-banner>
   <seccion-servicios></seccion-servicios>
  <ApiWeather></ApiWeather>

  </div>
</template>

<script>

import EncabezadoBanner from './components/EncabezadoBanner.vue'
import SeccionServicios from './components/SeccionServicios.vue'

import ApiWeather from './components/ApiWeather.vue'



export default {
  name: 'App',
  components: {

    EncabezadoBanner,
    SeccionServicios,
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


