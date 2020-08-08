<template>
  <div>
    <input placeholder="Ciudad" type="text" v-model="search">
     <b-button variant="success" v-on:click="setSearch">Buscar</b-button>
      <h5>{{city.name}}</h5>
    <b-table striped hover :items="items" :fields="fields"></b-table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'WeatherResponse',
    data(){
        return {
            fields: [],
            items: [],
            search:'',
            list: [],
            city: {}
        }
    },
    methods:{
        getTodos(buscar){
            var apiKey = '4d52b5b750d5a63fb5093668768e7960';
            axios.get(`http://api.openweathermap.org/data/2.5/forecast?q=${buscar}&appid=${apiKey}&units=metric&lang=sp`)
            .then(res=>{
                console.log(res)
                this.list= res.data.list
                this.city = res.data.city
                this.fields= ['fecha', 'temp_min','temp_max','pronostico'],
               res.data.list.forEach(el => {
                   this.items.push({
                       fecha: el.dt_txt,
                       temp_min: el.main.temp_min+'°C',
                       temp_max: el.main.temp_max+'°C',
                       pronostico: el.weather[0].description
                       })
               });
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