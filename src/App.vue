<template>
  <div id="app" class="container">
    <Encabezado titulo="Conversor de Unidades"/>
  </div>
</template>

<script>
import Encabezado from './components/Encabezado.vue'

export default {
  name: 'App',
  components: {
    Encabezado
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
