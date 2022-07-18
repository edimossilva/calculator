<template>
  <div class="hello">
    <h1>Calculator</h1>

    {{number1}} * {{number2}} =

    <input type="number" v-model="result"/>
    <input type="button" value="responder" v-on:click.exact="calculateOnClick"/>

  </div>
</template>

<script>
export default {
  name: 'CalculatorComponent',
  data() {
    return {
      number1: 1,
      number2: 2,
      result: 0
    }
  },
  methods: {
    calculateOnClick: function () {
      // `this` inside methods point to the Vue instance
      let isMultiplicationCorrect = (this.number1 * this.number2) == this.result
      if (isMultiplicationCorrect) {
        alert('Correct')
        this.generateNewNumbers()
      } else {
        alert('Incorrect')
      }
    },
    generateNewNumbers(){
      this.number1 = Math.floor(Math.random() * 100)
      this.number2 = Math.floor(Math.random() * 100)
      this.result = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
