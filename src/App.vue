<template>
  <div id="app">
   <encabezado-banner></encabezado-banner>
   <seccion-servicios></seccion-servicios>
  </div>
</template>

<script>
import EncabezadoBanner from './components/EncabezadoBanner.vue'
import SeccionServicios from './components/SeccionServicios.vue'

export default {
  name: 'App',
  components: {
    EncabezadoBanner,
    SeccionServicios
  }
}
</script>

