<template>
  <img class="fade-in " alt="Vue logo" src="https://images.pexels.com/photos/7184481/pexels-photo-7184481.jpeg?cs=srgb&dl=pexels-leonel-yedi-7184481.jpg&fm=jpg">

 <PokemonPageVue/>

</template>

<script>

import PokemonPageVue from './pages/PokemonPage.vue'


export default {
  name: 'App',
  components: {
    PokemonPageVue
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
img{
  height: 3%;
  width: 10%;
}
</style>
