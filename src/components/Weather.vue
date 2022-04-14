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

        <div class="w75 mb-4">
            <h3 class="text-center">Position : Paris</h3>
        </div>

        <div class="card text-center p-5">
            <p class="showed-text">Temperature : 20°</p>
            <p class="showed-text">Weather conditions : Cloudy</p>
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
             api_code: '2e0186d2418817dc5d083ed3d2e66647',
             url_search: 'api.openweathermap.org/data/2.5/weather?'
         }
     },
     method: {
     }
 }

</script>



<style scoped>

</style>
