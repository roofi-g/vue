<template>
  <div>
    <div class="display">
      <input v-model.number="operand1" type="number">
      <input v-model.number="operand2" type="number">
      = {{ result }}
    </div>
    <div class="keyboard">
      <button @click="sum">+</button>
      <button @click="sub">-</button>
      <button @click="mult">*</button>
      <button @click="div">/</button>
      <button @click="expo">**</button>
      <button @click="remainder">%</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalcComponent',
  data () {
    return {
      operand1: 0,
      operand2: 0,
      result: 0
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
      this.result = this.operand1 / this.operand2
    },
    expo () {
      this.result = this.operand1 ** this.operand2
    },
    remainder () {
      this.result = this.operand1 % this.operand2
    }
  }
}
</script>

<style scoped>

</style>
