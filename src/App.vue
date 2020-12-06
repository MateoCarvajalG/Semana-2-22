<template>
  <div id="app">

   <encabezado-banner></encabezado-banner>
   <seccion-servicios></seccion-servicios>
  <ApiWeather></ApiWeather>
  

    <h2>{{ tituloEquipo }}</h2>
    <div class="card-deck">
      <div class="card"  v-for = "(item , index) of team" :key = "index">
        <TeamCard v-bind:member = "item" /> 
      </div>
    </div>
    <pagefooter></pagefooter>

  </div>
</template>

<script>
import Pagefooter from './components/Pagefooter.vue'


import EncabezadoBanner from './components/EncabezadoBanner.vue'
import SeccionServicios from './components/SeccionServicios.vue'
import ApiWeather from './components/ApiWeather.vue'
import TeamCard from './components/TeamCard.vue'


export default {
  name: 'App',
  components: {


    EncabezadoBanner,
    SeccionServicios,
    ApiWeather,
    TeamCard,
    Pagefooter

  },

    data () {

      return{

        tituloEquipo : 'EQUIPO',
        team: [{
          codigo: 1,
          nombre: 'FRANCISCO ASTUDILLO',
          descripcion: 'Francisco Astudillo, quien actualmente es residente de la ciudad de Cali. Graduado como Ingeniero Ambiental en la Universidad del Valle y por ultimo, pero no menos importante, su deporte favorito es BMX.',
          rol: 'Tester',
          image: "./img/Francisco-Astudillo.jpg"
        },
        
        {
          codigo: 2,
          nombre: 'JULIAN JIMENEZ ORTIZ',
          descripcion: 'Julian Jimenez Ortiz, Ingeniero Geologo graduado en la Universidad Nacional de Colombia, actualmente se encuentra viviendo en la ciudad de Florencia, donde aprovecha el tiempo para practicar piano, manejar bicicleta y juagr volley.',
          rol: 'Desarrollador Front-End',
          image: './img/Julian-Jimenez-Ortiz.png'
        },

        {
          codigo: 3,
          nombre: 'KEWIN PASSOS G.',
          descripcion: 'Kewin Passos G. graduado de la Universidad Nacional de Colombia como Ingeniero Forestal y que actualmente es residente de la ciudad de Medellin, hoy en dia dedica parte de su tiempo a desarrollar actividades para cumplir la mision MINTIC 2022.',
          rol: 'Desarrollador FullStack',
          image: './img/Kewin-Passos-G.jpg'
        },

        {
          codigo: 4,
          nombre: 'MATEO CARVAJAL',
          descripcion: 'Mateo Carvajal, un amante de los motores y la tecnologia, logro graduarse como Ingeniero Mecatronico de la Universidad de Caldas, ademas de ser tecnologo en mecatronica automotriz con tan solo 25 años.',
          rol: 'Desarrollador backend',
          image: './img/Mateo-Carvajal.png'
        },

        {
          codigo: 5,
          nombre: 'CRISTIAN CABARCAS',
          descripcion: 'Cristian Cabarcas, quien actualmente es residente de la ciudad de Cartagena, se encuentra siguiendo los pasos de sus compañeros para lograr una profesion al igual que ellos, dedicando su tiempo al estudio.',
          rol: 'Arquitecto de Software',
          image: './img/Cristian-Cabarcas.jpg'
        }]
      }
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
  /* margin-top: 60px; */
}
  .card-deck{

    margin-left: 0px;
    margin-right: 0px;
  }  

  .card{

    height: 100%;
    border-radius: 10px;
  }

  h2{
    margin-top: 5px;
    text-align: center;
    background: rgba(11, 51, 1, 0.507);
    border-radius: 20px;
  }
  
</style>



