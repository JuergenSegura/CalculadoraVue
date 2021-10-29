<template>
  <div id="app text-center">
    <img alt="Vue logo" src="./assets/logo.png" height="75px" class="mx-auto d-block">
    <h2 class="text-center">Calculadora Vue</h2>
    <calculadora />
  </div>
</template>

<script>
import Calculadora from './components/Calculadora.vue'

export default {
  name: 'App',
  components: {
    Calculadora
  }
}
</script>


    Calculadora