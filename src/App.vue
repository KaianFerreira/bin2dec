<template>
  <div id="app">
    <input type="number" v-model="binaryNumber">
    {{converted}}
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data () {
    return {
      binaryNumber: '',
      converted: 0
    }
  },
  watch: {
    binaryNumber (teste) {
      let result = 0
      let start = 1
      let indexEnd = teste.length
      const end = teste.length
      while (start <= end) {
        console.log(start, end)
        result += Number(teste[start - 1]) * Math.pow(2, (indexEnd - 1))
        start++
        indexEnd--
      }
      this.converted = Number(result)
    }
  }

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
