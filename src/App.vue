<template>
  <Calculator/>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
#app {
  min-height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: white;
  background: linear-gradient(to bottom, #00b4db, #0083b0);
}
</style>
