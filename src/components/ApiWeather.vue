<template>
    <div id="clima">
        <div id="weatherContainer">
            <div id='weatherContainer__temperatura'> 
                <button @click="findMe()">Mostrar clima</button>
            </div>
            <div></div>
            <div></div>
            <div></div>

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
        resultJson : []
      }
  },

  methods : {
    
    findMe(){

        var output = document.getElementById("clima");
        if (!navigator.geolocation) {
        output.innerHTML = "<p>Tu navegador no soporta geolocalizacion</p>";
        } 


        function localizacion(posicion) {
        const lat = posicion.coords.latitude;
        const lon = posicion.coords.longitude;
        console.log(lat);
        console.log(lon);
        apiWeather(lat,lon);

        }
        function error() {
        output.innerHTML = "<p>No se pudo obtener tu ubicacion</p>";
        }


        async function  apiWeather(latitude,longitude){
        const result =  await fetch ( `http://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&appid=725c3e54a024870fec08bf0537d47a9c&units=metric`,{
        method :'GET',
        })

        let resultJson = await result.json()

        if (result.ok){
        console.log(resultJson);
        // console.log(resultJson.main.temp);
        printOnScreen(resultJson);
        }
        }

        function printOnScreen(dataText){
           const weatherContainer = document.getElementById('weatherContainer__temperatura')


            const {name,main,weather,wind,sys} = dataText
            console.log(name,main,weather,wind);

            
            
            const city = document.createElement('h2');
            city.textContent = 'Su ciudad es  '+name +', '+sys.country+'.';

            const temp = document.createElement('h3')
            temp.textContent = 'La temperatura es: '+ main.temp + ' °C';

            
            weatherContainer.appendChild(city);
            weatherContainer.appendChild(temp);     
        }


        navigator.geolocation.getCurrentPosition(localizacion, error);
    },




    



  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>