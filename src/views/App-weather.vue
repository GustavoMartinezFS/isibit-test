<template>
  <div id="app">
    <h1>Te vas de viaje?</h1>
    <p>Averigua si te conviene quedarte unos dias mas <br> o como estara el clima en tu destino</p>
     <b-card >
       <b-card-group deck>
          <b-card header="Origen">   
            <WeatherResponse ubi='true'/>
         </b-card>
          <b-card header="Destino">  
            <WeatherResponse />
          </b-card>
        </b-card-group>
     </b-card>
  </div>
</template>

<script>
import WeatherResponse from '@/components/WeatherResponse.vue'

export default {
  name: 'Appweather',
  components: {
  WeatherResponse
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
