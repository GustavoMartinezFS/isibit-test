<template>
  <div>
    <input placeholder="Ciudad" type="text" v-model="search" class="mr-2">
     <b-button variant="success" v-on:click="setSearch">Buscar</b-button>
     <b-button @click="getUbi" class="ml-2" v-if="ubi">Mi ubicacion</b-button>
     <p>{{error}}</p>  
      <h5 class="mt-5">{{city.name}}</h5>
    <b-table striped hover :items="items" :fields="fields" >
         <template v-slot:cell(icon)='data'>
       <b-img :src='`${data.value}`'></b-img> 
      </template>
    </b-table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'WeatherResponse',
    props: {
    ubi: String
  },
    data(){
        return {
            fields: [],
            items: [],
            search:'',
            list: [],
            city: {},
            error: ''
        }
    },
    methods:{
        getForecast(buscar){
            var apiKey = '4d52b5b750d5a63fb5093668768e7960';
            axios.get(`https://api.openweathermap.org/data/2.5/forecast?q=${buscar}&appid=${apiKey}&units=metric&lang=sp`)
            .then(res=>{
               this.list= res.data.list
                this.city = res.data.city
                this.fields= ['fecha', 'temp_min','temp_max','pronostico',{ key: 'icon', label: 'Icon' }],
                this.items=[]
               res.data.list.forEach(el => {
                   this.items.push({
                       fecha: el.dt_txt,
                       temp_min: el.main.temp_min+'°C',
                       temp_max: el.main.temp_max+'°C',
                       pronostico: el.weather[0].description,
                       icon: `https://openweathermap.org/img/wn/${el.weather[0].icon}@2x.png`
                       })
               });
            })
            .catch(e => console.log(e))
        },
        setSearch(){
           this.getForecast(this.search)
        },
        getUbi(){
          if (!navigator.geolocation){
                this.error = "Geolocation is not supported by your browser";
                return;
              }
               var _this = this
              function success(position) {
               var lat = position.coords.latitude;
                 var long = position.coords.longitude;
               _this.error=''
                var apiKey = '4d52b5b750d5a63fb5093668768e7960';
                axios.get(`https://api.openweathermap.org/data/2.5/forecast?lat=${lat}&lon=${long}&appid=${apiKey}&units=metric&lang=sp`)
                .then(res=>{
                  _this.list= res.data.list
                    _this.city = res.data.city
                    _this.fields= ['fecha', 'temp_min','temp_max','pronostico',{ key: 'icon', label: 'Icon' }],
                    _this.items=[]
                   res.data.list.forEach(el => {
                       _this.items.push({
                           fecha: el.dt_txt,
                           temp_min: el.main.temp_min+'°C',
                           temp_max: el.main.temp_max+'°C',
                           pronostico: el.weather[0].description,
                           icon: `http://openweathermap.org/img/wn/${el.weather[0].icon}@2x.png`
                           })
                   });
                })
                .catch(e => console.log(e))
              }
              function error() {
                _this.error = "Unable to retrieve your location";
              }
              this.error = "Locating…";
                  //appid=439d4b804bc8187953eb36d2a8c26a02 id de example 
              navigator.geolocation.getCurrentPosition(success, error);
        }
    }
}
</script>