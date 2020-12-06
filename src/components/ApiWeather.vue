<template>
  <div id="clima" class="container-fluid mt-5" >
    <h3 class="h1 bg-success text-white mt-2 mb-2"> Metereología</h3>
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-default">Ingrese la Ciudad</span>
      </div>
      <input
        type="text"
        class="form-control d-flex justify-content-center align-itemscenter" aria-describedby="inputGroup-sizing-default"
        v-model="ubicacion"
        v-on:keyup.enter="getText"
      />
    </div>
    <button type="button" class="btn btn-secondary btn-lg" v-on:click="getText">Mostrar clima</button>
    <!-- <pre>{{$data}}</pre> -->
    <div id="weatherContainer" class="row mt-md-5 mt-sm-5 mt-xs-5">
      <div id="weatherContainer__temperatura" class="col-lg-6 col-xs-12 border">
        <div class="d-flex justify-content-center align-itemscenter">
          <div class="p-2">
            <h4>Temperatura</h4>
            <hr />
            <div class="text-justify">
              <h5>
                Ciudad: {{ resultJson.name }}, {{ resultJson.sys.country }}.
              </h5>
              <h5>La temperatura es de {{ resultJson.main.temp }} °C</h5>
              <h5>Sensación Térmica {{ resultJson.main.feels_like }} °C</h5>
              <h5>La presión es {{ resultJson.main.pressure }} hPa</h5>
              <i class="fa fa-lg fa-info mr-3" ></i>
              <a v-bind:href="URLtemp" target="_blank" class="d-inline "> <input type="button" class="btn btn-link btn-outline-success btn-lg font-italic Italica" value= "More Info">
              </a>
            </div>
          </div>
          <div class="p-3">
            <img
              src="../assets/temperatura.jpg"
              alt="Imagen de Clima"
              class="img-thumbnail"
              width="300 "
              height="200"
            />
          </div>
        </div>
        <div class="d-flex container-fluid justify-content-center pb-2 mt-n2">
          <!-- <a
            href="#"
            target="_blank"
            class="btn btn-primary btn-outline-dark font-italic Italica"
            >Info</a
          > -->
        </div>
      </div>
<!-- //---------------------------------- -->
      <div id="weatherContainer__" class="col-lg-6 col-xs-12 border">
        <div class="d-flex justify-content-center align-itemscenter">
          <div class="p-2">
            <h4>Estado del clima.</h4>
            <hr />
            <div class="text-justify">
              <h3 class= "text-center"> {{resultJson.weather[0].main}} 
                  <img v-bind:src="URLicon" class="img-responsive" alt="">
              </h3>
              <h3>Description:</h3>
              <h4 class="text-capitalize text-center ">{{resultJson.weather[0].description}}</h4>
              <i class="fa fa-lg fa-info mr-3" ></i>
              <a v-bind:href="URLlluvia" target="_blank" class="d-inline "> <input type="button" class="btn btn-link btn-outline-success btn-lg font-italic Italica" value= "More Info">
              </a>
          
            </div>
          </div>
          <div class="p-3">
            <img
              src="../assets/clima.jpg"
              alt="Imagen de Clima"
              class="img-thumbnail"
              width="300 "
              height="200"
            />
          </div>
        </div>
        <div class="d-flex container-fluid justify-content-center pb-2 mt-n2">
         
        </div>
      </div>
<!-- ---------------------------------------------------- -->
      <div id="weatherContainer__condiciones" class="col-lg-6 col-xs-12 border">
        <div class="d-flex justify-content-center align-itemscenter">
          <div class="p-2">
            <h4>Condiciones Ambientales</h4>
            <hr />
            <div class="text-justify">
              <h5>Humedad Relativa: {{ resultJson.main.humidity }} %</h5>
              <h5>Velocidad del Viento: {{ resultJson.wind.speed }} mph</h5>
              <h5>Dirección del Viento: {{ resultJson.wind.deg }} grados</h5>
              <i class="fa fa-lg fa-info mr-3" ></i>
              <a v-bind:href="URLhumedad" target="_blank" class="d-inline "> <input type="button" class="btn btn-link btn-outline-success btn-lg font-italic Italica" value= "More Info">
              </a>
            </div>
          </div>
          <div class="p-3">
            <img
              src="../assets/wind.png"
              alt="Imagen de Clima"
              class="img-thumbnail"
              width="300 "
              height="200"
            />
          </div>
        </div>
        <div class="d-flex container-fluid justify-content-center pb-2 mt-n2">
        </div>
      </div>

      <div id="weatherContainer__" class="col-lg-6 col-xs-12 border">
        <div class="d-flex justify-content-center align-itemscenter">
          <div class="p-2" >
            <h4>Salida y Puesta del sol</h4>
            <hr />
            <h3> Fecha: {{fechaA}}</h3>
            <hr>
              <div id="horaAmanecer" class="float-left mr-5" >
                  <img src="../assets/amanecer.png" 
                  alt=""
                  class="img-thumbnail"
                  width="150"
                  height="150">
                  <h3>Salida del sol <br> {{horaA}}:{{minutosA}}:{{segundosA}} </h3>


              </div>
              <div id="horaAtardecer" class="float-right ml-5" >
                <img src="../assets/atardecer.jpg" 
                  alt=""
                  class="img-thumbnail"
                  width="150"
                  height="150">
                  <h3>Puesta del sol <br> {{horaAt}}:{{minutosAt}}:{{segundosAt}} </h3>
              </div>
            </div>
         
          
        </div>
        <div class="d-flex container-fluid justify-content-center pb-2 mt-2">
          <i class="fa fa-lg fa-info mr-3 mt-3" ></i>
              <a href="https://www.google.com/" target="_blank" class="d-inline "> <input type="button" class="btn btn-link btn-outline-success btn-lg font-italic Italica" value= "More Info">
              </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ApiWeather',
  props: {
    msg: String
  },
  data(){
      return{
        ubicacion : '',
        resultJson: null,
        URLicon : null,
        URLtemp: null,
        URLhumedad: null,
        URLlluvia: null ,
        fechaA: null,
        horaA: null,
        minutosA: null,
        segundosA: null,
        fechaAt: null,
        horaAt: null,
        minutosAt: null,
        segundosAt: null

      }
  },
    mounted: async function(){
        
        const result =  await fetch ( `http://api.openweathermap.org/data/2.5/weather?q=bogota&appid=725c3e54a024870fec08bf0537d47a9c&units=metric`,{
        method :'GET',
        })
        this.resultJson = await result.json()
        if (result.ok){
        console.log(this.resultJson);
        this.URLicon = `http://openweathermap.org/img/wn/${this.resultJson.weather[0].icon}@2x.png` ;
        this.URLtemp = `https://www.windy.com/es/-Temperatura-temp?temp,${this.resultJson.coord.lat},${this.resultJson.coord.lon},6,i:pressure`;
        this.URLhumedad = `https://www.windy.com/es/-Humedad-rh?rh,${this.resultJson.coord.lat},-${this.resultJson.coord.lon},7`
        this.URLlluvia= `https://www.windy.com/es/-Acumulaci%C3%B3n-de-lluvia-rainAccu?rainAccu,${this.resultJson.coord.lat},${this.resultJson.coord.lon},7,m:dP5ad4l`

        let horaAmanecer = this.resultJson.sys.sunrise + this.resultJson.timezone
        let Fecha = new Date(horaAmanecer *1000);
        this.fechaA = Fecha.getDate() +'/'+ (Fecha.getMonth()+1 )+'/'+ Fecha.getFullYear() 
        this.horaA = Fecha.getUTCHours().toString().padStart(2,0);
        this.minutosA= Fecha.getUTCMinutes().toString().padStart(2,0);
        this.segundosA = Fecha.getUTCSeconds().toString().padStart(2,0);

        let horaAtardecer = this.resultJson.sys.sunset + this.resultJson.timezone ;
        let FechaAt = new Date(horaAtardecer *1000);
        this.fechaAt = FechaAt.getDate() +'/'+ (Fecha.getMonth()+1 )+'/' + Fecha.getFullYear() 
        this.horaAt = FechaAt.getUTCHours().toString().padStart(2,0);
        this.minutosAt= FechaAt.getUTCMinutes().toString().padStart(2,0);
        this.segundosAt = FechaAt.getUTCSeconds().toString().padStart(2,0);

        }

        
    },
  
  methods : {

      getText: async function(){
        console.log(this.ubicacion)
        
        const result =  await fetch ( `http://api.openweathermap.org/data/2.5/weather?q=${this.ubicacion}&appid=725c3e54a024870fec08bf0537d47a9c&units=metric`,{
        method :'GET',
        })
        this.resultJson = await result.json()
        if (result.ok){
        console.log(this.resultJson);
        
        this.URLicon = `http://openweathermap.org/img/wn/${this.resultJson.weather[0].icon}@2x.png` ;
        this.URLtemp = `https://www.windy.com/es/-Temperatura-temp?temp,${this.resultJson.coord.lat},${this.resultJson.coord.lon},6,i:pressure`;
        this.URLhumedad = `https://www.windy.com/es/-Humedad-rh?rh,${this.resultJson.coord.lat},${this.resultJson.coord.lon},7`
        this.URLlluvia= `https://www.windy.com/es/-Acumulaci%C3%B3n-de-lluvia-rainAccu?rainAccu,${this.resultJson.coord.lat},${this.resultJson.coord.lon},7,m:dP5ad4l`
        console.log(this.URLicon)
        console.log(this.URLtemp);


        let horaAmanecer = this.resultJson.sys.sunrise + this.resultJson.timezone
        let Fecha = new Date(horaAmanecer *1000);
        this.fechaA = Fecha.getDate() +'/'+ (Fecha.getMonth()+1 )+'/' + Fecha.getFullYear() 
        this.horaA = Fecha.getUTCHours().toString().padStart(2,0);
        this.minutosA= Fecha.getUTCMinutes().toString().padStart(2,0);
        this.segundosA = Fecha.getUTCSeconds().toString().padStart(2,0);

        let horaAtardecer = this.resultJson.sys.sunset + this.resultJson.timezone ;
        let FechaAt = new Date(horaAtardecer *1000);
        this.fechaAt = FechaAt.getDate() +'/'+ (Fecha.getMonth()+1 )+'/' + Fecha.getFullYear() 
        this.horaAt = FechaAt.getUTCHours().toString().padStart(2,0);
        this.minutosAt= FechaAt.getUTCMinutes().toString().padStart(2,0);
        this.segundosAt = FechaAt.getUTCSeconds().toString().padStart(2,0);
        }

        }
      
      // cambiarHoraAmanecer(unix)
      //       {
      //         this.fecha = new Date(unix*1000);
      //         this.hora = fecha.getUTCHours().toString().padStart(2,0);
      //         this.minutos= fecha.getUTCMinutes().toString().padStart(2,0);
      //         this.segundos = fecha.getUTCSeconds().toString().padStart(2,0);

      //       }
      
      
    }
  }


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>