<template>
  <div id="app">
    <div style="width:50%">
    <WeatherResponse uso='origen'/>
    </div>
    <div style="width:50%">
    <WeatherResponse uso='destino'/>
    </div>
  </div>
</template>

<script>
import WeatherResponse from './components/WeatherResponse.vue'

export default {
  name: 'App',
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
