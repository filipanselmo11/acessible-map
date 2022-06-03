<template>
  <div>
    <mapa-component></mapa-component>
  </div>
</template>

<script>
import MapaComponent from './components/MapaComponent.vue'

export default {
  name: 'App',
  components: {
    MapaComponent
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
