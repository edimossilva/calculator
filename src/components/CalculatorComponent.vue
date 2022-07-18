<template>
  <div class="options-row">
    <div class="option">
      <span>Fácil</span>
    </div>

    <div class="option">
      <span>Médio</span>
    </div>

    <div class="option-selected">
      <span>Difícil</span>
    </div>
  </div>

  <div class="container">
    <div>
      <h1>Quanto é..</h1>
      <div class="row-numbers">
        <span class="number-sm">{{number1}}</span>
        <span class="mult"> x </span>
        <span class="number-sm">{{number2}}</span>
      </div>
      <input type="number" placeholder="Digite aqui" class="response-input" v-model="result" />
      <button class="response-button" v-on:click.exact="calculateOnClick">RESPONDER</button>

      <!-- <div v-if="offensive === offensives.itachi.milestone" class="offensive">
        <span>Ofensiva do naturo! você acertou <strong>{{offensives.itachi.milestone}} vezes</strong> </span>
        <img
          class="meme-picture"
          src={{offensives.itachi.img}} alt="">
      </div> -->
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
      result: '',
      level: 'dificil',
      offensive: 10,
      actualOffensive: null
    }
  },
  methods: {
    calculateOnClick: function () {
      // `this` inside methods point to the Vue instance
      let isMultiplicationCorrect = (this.number1 * this.number2) === this.result
      if (isMultiplicationCorrect) {
        this.$toast.success(`Correct`, {duration:1500});
        this.generateNewNumbers()
        this.upgradeOffensive()
        this.getMilestone()
      } else {
        this.$toast.error(`Incorrect`, {duration:1500});
        this.result = ''
      }
    },
    generateNewNumbers(){
      this.number1 = Math.floor(Math.random() * this.rangePerLevel1())
      this.number2 = Math.floor(Math.random() * this.rangePerLevel2())
      this.result = ''
    },
    upgradeOffensive(){
      this.offensive = this.offensive + 1
    },
    getMilestone(){
      const milestones = {
        5: {
          name: 'Naruto',
          img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSYn3eDZQlpIWYKhbTjl2UaBKZc626TGdBCzQ&usqp=CAU'
        },
        10: {
          name: 'Naruto',
          img: 'https://i.pinimg.com/736x/1e/45/a2/1e45a2385a35bc798ffc07237ffaaeee.jpg'
        }
      }

      this.actualOffensive = milestones[this.offensive]
      console.log(this.actualOffensive)
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
.container {
  padding: 30px;
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
.options-row {
  display: flex;
  flex-direction: row;
  padding: 0px 30px;
  justify-content: space-between;
}
.option {
  padding: 16px;
  font-size: 14px;
  background: #090a0e;
  border-radius: 10px;
}

.option-selected {
  padding: 16px;
  font-size: 14px;
  background: #fdfdff;
  border-radius: 10px;
  color: #22252d;
  font-weight: bold;
}

.offensive {
  margin-top: 20px;
  text-align: center;
}
.meme-picture {
  margin-top: 8px;
}
</style>
