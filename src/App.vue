<template>
  <div id="app" class="container">
    <Header titulo="Conversor de Unidades"/>
    <BaseForm />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import BaseForm from './components/BaseForm.vue'

export default {
  name: 'App',
  components: {
    Header,
    BaseForm
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
