<template>
  <CalculatorComponent/>
</template>

<script>
import CalculatorComponent from './components/CalculatorComponent.vue'

export default {
  name: 'App',
  components: {
    CalculatorComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fdfdff;
  margin-top: 60px;
}

body {
  background-color: #22252d;
}
</style>
