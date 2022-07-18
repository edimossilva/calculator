<template>
  <!-- <div class="hello">
    <h1>Calculator</h1>

    {{number1}} * {{number2}} =

    <input type="number" v-model="result"/>
    <input type="button" value="responder" v-on:click.exact="calculateOnClick"/>

  </div> -->
  <div class="container">
    <div>
      <h1>Quanto é..</h1>
      <div class="row-numbers">
        <span class="number-sm">{{number1}}</span>
        <span class="mult"> x </span>
        <span class="number-sm">{{number2}}</span>
      </div>
      <input type="number" class="response-input" v-model="result" />
      <button class="response-button" v-on:click.exact="calculateOnClick">RESPONDER</button>
    </div>
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
.container {
  padding: 0px 30px;
  text-align: right;
}
.number-sm {
  font-size: 18px;
  font-weight: bold;
}
.row-numbers {
  display: flex;
  align-items: center;
  justify-content: end;
}
.mult {
  font-size: 14px;
  font-weight: bold;
  color: #d66968;
  padding: 0px 10px;
}
.response-input {
  width: 100%;
  background: transparent;
  color: #fff;
  font-size: 30px;
  margin-top: 20px;
  border: none;
  border-bottom: 2px solid #42b983;
}

.response-button {
  background-color: #42b983;
  width: 100%;
  border: none;
  margin-top: 20px;
  padding: 8px;
  border-radius: 6px;
  color: #fff;
  letter-spacing: 2px;
  font-size: 12px;
}
</style>
