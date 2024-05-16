<script setup>
import Navbar from './components/NavBar.vue'
import IntroScreen from './components/Intro-Screen.vue'
import Alquiler from './components/Alquiler.vue'
import Venta from './components/Venta.vue'
import FormContacto from './components/FormContacto.vue'
</script>

<template>
  <Navbar />
  <div class="wrapper">
    <IntroScreen />
    <Venta />
    <Alquiler />
    <FormContacto />
  </div>
</template>

<style scoped>
.wrapper {
  width: 100%;
  max-width: 100%;
  background-color: #295264;
  overflow-x: hidden;
  height: 100%;
  padding-left: 5%;
  padding-right: 5%;
}
</style>
