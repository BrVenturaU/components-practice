<template>
    <!-- Encabezado de la página-->
    <b-row>
        <b-col cols="12">
            <img alt="App Logo" class="logo rounded-circle shadow mb-3" src="@/assets/images/logo.jpg">
            <h1>{{titulo}}</h1>
        </b-col>
    </b-row>
</template>

<script>
export default {
    name: 'Encabezado',
    // Propiedades compartidas
    props: {
        titulo: String
  }
}
</script>

<style scoped>
/* Estilos personalizados */
    .logo{
        width: 192px;
        height: 192px;
    }
</style>