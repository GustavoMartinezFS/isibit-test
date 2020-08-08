<template>
  <div id="app">
    <geoloc/>
    <h1>Te vas de viaje?</h1>
    <p>Averigua si te conviene quedarte unos dias mas o como estara el clima en tu destino</p>
     <b-card >
       <b-card-group deck>
          <b-card header="Origen">   
            <WeatherResponse />
         </b-card>
          <b-card header="Destino">  
            <WeatherResponse />
          </b-card>
        </b-card-group>
     </b-card>
  </div>
</template>

<script>
import WeatherResponse from './components/WeatherResponse.vue'
import geoloc from './components/geoloc.vue'

export default {
  name: 'App',
  components: {
  WeatherResponse,
  geoloc
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
