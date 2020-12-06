<template>
    <div id="clima">
        <input type="text" class="form-control mt-5" v-model="ubicacion" v-on:keyup.enter="getText">
            <button v-on:click="getText">Mostrar clima</button>
                <!-- <pre>{{$data}}</pre> -->
        <div id="weatherContainer">
            
            <div id='weatherContainer__temperatura'> 
                
                
                <h2>Ciudad: {{resultJson.name}}, {{resultJson.sys.country}}.</h2>
                <h2>La temperatura es de {{resultJson.main.temp}} °C</h2>
                <h2>Sensacion Termica {{resultJson.main.feels_like}}</h2>
                <h2>La presion es {{resultJson.main.pressure}} hPa</h2>
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
        ubicacion : '',
        resultJson: null
      }
  },
    mounted: async function(){
        
        const result =  await fetch ( `http://api.openweathermap.org/data/2.5/weather?q=bogota&appid=725c3e54a024870fec08bf0537d47a9c&units=metric`,{
        method :'GET',
        })
        this.resultJson = await result.json()
        if (result.ok){
        console.log(this.resultJson);
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
        }
        
      
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>