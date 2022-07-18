<template>
  <div class="hello">
    <h1>Calculator 2</h1>
    <input type="radio" id="facil" value="facil" v-model="level">
    <label for="one">Facil</label>

    <input type="radio" id="medio" value="medio" v-model="level">
    <label for="two">Medio</label>

    <input type="radio" id="dificil" value="dificil" v-model="level">
    <label for="two">Dificil</label>
    {{level}}
    <br>
    <span>Picked: {{ picked }}</span>

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
      result: '',
      level: 'dificil'
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
      this.number1 = Math.floor(Math.random() * this.rangePerLevel1())
      this.number2 = Math.floor(Math.random() * this.rangePerLevel2())
      this.result = ''
    },
    rangePerLevel1(){
      let levels = {
        'facil': 10,
        'medio': 10,
        'dificil': 100
      }
      return levels[this.level]
    },
    rangePerLevel2(){
      let levels = {
        'facil': 10,
        'medio': 100,
        'dificil': 100
      }
      return levels[this.level]
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
