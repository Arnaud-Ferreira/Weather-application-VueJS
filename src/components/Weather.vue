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
            <div class="card text-center p-5">
                <p class="showed-text">Temperature : {{ weather.main.temp.toFixed() }}°</p>
                <p class="showed-text">Weather conditions : {{ weather.weather[0].description }}</p>
             </div>
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
             api_code: 'f63bb6484c79154fe4d2602c4da61ec9',
             url_search: 'https://api.openweathermap.org/data/2.5/weather?'
         }
     },
     methods: {
         goWeather(e){
             if(e.key == "Enter") {

                 axios
                 .get(`${this.url_search}q=${this.request}&units=metric&appid=${this.api_code}&lang=en`)
                 .then(response => {
                     this.weather = response.data;
                 })
                //  To reset the input after enter
                    this.request = '';
             }
         }
     }
 }

</script>



<style scoped>

h1 {
    text-align: center;
}

label {
    display: flex;
    justify-content: center;
    margin-top: 2.5rem;
    font-size: 1.5rem;
}

.mt-3 {
    margin-top: 2rem!important;
    padding: 1rem;
}

.text-center {
    margin-bottom: 1.5rem;
}

h3 {
    font-style: italic;
}

.showed-text {
    font-size: 30px;
    font-weight: 400;
    line-height: 1.2;
}

</style>
