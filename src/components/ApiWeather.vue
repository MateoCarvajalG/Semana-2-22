<template>
  <div id="clima" class="container-fluid">
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
              <h5>Sensacion Termica {{ resultJson.main.feels_like }} °C</h5>
              <h5>La presion es {{ resultJson.main.pressure }} hPa</h5>
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
          <a
            href="#"
            target="_blank"
            class="btn btn-primary btn-outline-dark font-italic Italica"
            >Info</a
          >
        </div>
      </div>
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
              <h5>Sensacion Termica {{ resultJson.main.feels_like }}</h5>
              <h5>La presion es {{ resultJson.main.pressure }} hPa</h5>
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
          <a
            href="#"
            target="_blank"
            class="btn btn-primary btn-outline-dark font-italic Italica"
            >Info</a
          >
        </div>
      </div>

      <div id="weatherContainer__condiciones" class="col-lg-6 col-xs-12 border">
        <div class="d-flex justify-content-center align-itemscenter">
          <div class="p-2">
            <h4>Condiciones Ambientales</h4>
            <hr />
            <div class="text-justify">
              <h5>Humedad Relativa: {{ resultJson.main.humidity }} %</h5>
              <h5>Velocidad del Viento: {{ resultJson.wind.speed }} mph</h5>
              <h5>Dirección: {{ resultJson.wind.deg }} grados</h5>
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
          <a
            href="#"
            target="_blank"
            class="btn btn-primary btn-outline-dark font-italic Italica"
            >Info</a
          >
        </div>
      </div>
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
              <h5>Sensacion Termica {{ resultJson.main.feels_like }}</h5>
              <h5>La presion es {{ resultJson.main.pressure }} hPa</h5>
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
          <a
            href="#"
            target="_blank"
            class="btn btn-primary btn-outline-dark font-italic Italica"
            >Info</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ApiWeather",
  props: {
    msg: String,
  },
  data() {
    return {
      ubicacion: "",
      resultJson: null,
    };
  },
  mounted: async function () {
    const result = await fetch(
      `http://api.openweathermap.org/data/2.5/weather?q=bogota&appid=725c3e54a024870fec08bf0537d47a9c&units=metric`,
      {
        method: "GET",
      }
    );
    this.resultJson = await result.json();
    if (result.ok) {
      console.log(this.resultJson);
    }
  },

  methods: {
    getText: async function () {
      console.log(this.ubicacion);

      const result = await fetch(
        `http://api.openweathermap.org/data/2.5/weather?q=${this.ubicacion}&appid=725c3e54a024870fec08bf0537d47a9c&units=metric`,
        {
          method: "GET",
        }
      );
      this.resultJson = await result.json();
      if (result.ok) {
        console.log(this.resultJson);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>