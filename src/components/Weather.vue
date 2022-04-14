<template>
    <div class="container">

        <h1 class="my-4">Weather application with Vue Js</h1>

        <div class="form-groupe mb-5">
            <label for="position">Enter a city name</label>
            <input
            id="position"
            type="text"
            class="form-control mt-3"
            v-model="request"
            v-on:keypress="goWeather"
            >
        </div>

        <div class="w75 mb-4" v-if="weather">
            <h3 class="text-center">Location : {{ weather.name }}</h3>
        </div>

        <div class="card text-center p-5">
            <p class="showed-text">Temperature : {{ weather.main.temp }}°</p>
            <p class="showed-text">Weather conditions : {{ weather.weather[0].description }}</p>
        </div>
    </div>
</template>



<script>
import axios from 'axios'

 export default {
     name: 'WeatherComp',
     data() {
         return {
             request: '',
             weather: undefined,
             api_code: '3604758d7467cfd1a0f161a64027236f',
             url_search: 'https://api.openweathermap.org/data/2.5/weather?'
         }
     },
     methods: {
         goWeather(event){
             if(event.key == "Enter") {

                 axios
                 .get(`${this.url_search}q=${this.request}&units=metric&
                 APPID=${this.api_code}&lang=fr`)
                 .then(response => {
                     this.weather = response.data;
                 })
                 this.request = ''
             }
         }
     }
 }

</script>



<style scoped>

.showed-text {
    font-size: 30px;
    font-weight: 400;
    line-height: 1.2;
}

</style>
