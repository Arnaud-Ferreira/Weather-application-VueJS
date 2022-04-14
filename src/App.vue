<template>
  <div class="app">
    <weather />
  </div>
</template>


<script>
import Weather from './components/Weather.vue'

export default {
  name: 'App',
  components: {
    'weather': Weather
  }
}

</script>



<style>
 body {
   background: #C9D6FF;
   background: linear-gradient(to right, #c9d6ff, #e2e2e2);
 }
</style>
