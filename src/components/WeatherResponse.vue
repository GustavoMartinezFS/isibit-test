<template>
  <div>
    <input type="text" v-model="search">Ciudad de {{uso}}
      <button v-on:click="setSearch">Buscar</button>
      <table>
          <tbody>
              <tr>{{city.name}}</tr>
              <tr v-for="dia in list" :key="dia.dt">
                  <td>Dia y hora: {{dia.dt_txt}}</td>
                  <td>Temp min: {{dia.main.temp_min}}</td>
                  <td>Temp max: {{dia.main.temp_max}}</td>
                  <td>Pronostico: {{dia.weather[0].description}}</td>
              </tr>
          </tbody>
      </table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'WeatherResponse',
    props:{
        uso: String
    },
    data(){
        return {
            search:'',
            list: [],
            city: {}
        }
    },
    methods:{
        getTodos(buscar){
            var apiKey = '4d52b5b750d5a63fb5093668768e7960';
            axios.get(`http://api.openweathermap.org/data/2.5/forecast?q=${buscar}&appid=${apiKey}`)
            .then(res=>{
                console.log(res)
                this.list= res.data.list
                this.city = res.data.city
            })
            .catch(e => console.log(e))
        },
        setSearch(){
           this.getTodos(this.search)
        }
    }
}
</script>

<style>

</style>