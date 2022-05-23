<template>
  <div>
    <div class="display">
      <input v-model.number="operand1" type="number">
      <input v-model.number="operand2" type="number">
      = {{ result }}
    </div>
    <div class="keyboard">
      <button v-for="operand in operands" @click="calculate(operand)" v-bind:key="operand" v-bind:title="operand">
        {{ operand }}
      </button>
    </div>
    <div v-if="error">Ошибка! {{ error }}</div>
    <div>
      <div class="checkbox">
        <input type="checkbox" id="checkbox" v-model="checked">
        <label>Отобразить электронную клавиатуру</label>
      </div>
      <div v-if="checked===true">
        <div>
          <button v-for="(item, index) in myCollection" v-bind:key="index" @click="writeInInput(item)">{{ item }}</button>
          <button v-on:click="deleteInInput">←</button>
        </div>
        <div>
          <input type="radio" id="one" value="operand1" v-model="picked">
          <label for="one">Операнд 1</label>
          <input type="radio" id="two" value="operand2" v-model="picked">
          <label for="two">Операнд 2</label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalcComponent',
  data () {
    return {
      operands: ['+', '-', '*', '/'],
      operand1: 0,
      operand2: 0,
      result: 0,
      error: '',
      checked: false,
      myCollection: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      picked: 'operand1'
    }
  },
  methods: {
    sum () {
      this.result = this.operand1 + this.operand2
    },
    sub () {
      this.result = this.operand1 - this.operand2
    },
    mult () {
      this.result = this.operand1 * this.operand2
    },
    div () {
      const { operand1, operand2 } = this
      if (operand2 === 0) {
        this.error = 'На 0 делить нельзя!'
      } else {
        this.result = operand1 / operand2
      }
    },
    calculate (operation = '+') {
      this.error = ''
      switch (operation) {
        case '+':
          this.sum()
          break
        case '-':
          this.sub()
          break
        case '*':
          this.mult()
          break
        case '/':
          this.div()
          break
      }
    },
    setOperandValue (string) {
      let number = parseInt(string)
      if (isNaN(number)) number = 0
      if (this.picked === 'operand1') {
        this.operand1 = number
      } else {
        this.operand2 = number
      }
    },
    writeInInput (i) {
      const string = (this.picked === 'operand1' ? this.operand1 : this.operand2).toString() + i.toString()
      this.setOperandValue(string)
    },
    deleteInInput () {
      const string = (this.picked === 'operand1' ? this.operand1 : this.operand2).toString().slice(0, -1)
      this.setOperandValue(string)
    }
  }
}
</script>

<style scoped>
.checkbox {
  margin-top: 50px;
  margin-bottom: 10px;
}
</style>
