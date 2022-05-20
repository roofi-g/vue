<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <CalcComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import CalcComponent from '@/components/Calc.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    CalcComponent
  }
}
</script>
