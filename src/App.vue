<template>
  <div id="app">
    <Header headText="Wills Vue.js Calculator" />
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'
import Header from "@/components/Header";

export default {
  name: 'App',
  components: {
    Calculator,
    Header
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
