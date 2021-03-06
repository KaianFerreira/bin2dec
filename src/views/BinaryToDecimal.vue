<template>
  <section>
    <div class="content">
      <span class="title">Bin2Dec</span>
      <div class="label">Insira um número binário, e receba uma resposta em decimal</div>
      <input type="text" v-model="binaryNumber">
      <div class="result" >
        <span class="value" v-if="!isNaN(converted) && binaryNumber.length > 0">{{converted}}</span>
        <span v-if="isNaN(converted)">{{converted}}</span>
      </div>
    </div>
  </section>
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
    binaryNumber (number) {
      let result = 0
      let start = 1
      let indexEnd = number.length
      const end = number.length
      while (start <= end) {
        result += Number(number[start - 1]) * Math.pow(2, (indexEnd - 1))
        start++
        indexEnd--
      }
      if (!isNaN(number)) {
        if (number.search(/([2-9])+/g) > -1) this.converted = 'Você inseriu um dígito não binário, por favor insira apenas 0 ou 1'
        else this.converted = Number(result)
      } else {
        this.converted = 'Você inseriu um dígito não binário, por favor insira apenas 0 ou 1'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 75vw;
    max-width: 500px;
    .title {
      font-size: 3em;
      font-weight: 600;
      line-height: 30px;
    }
    .label, .result {
      margin: 15px;
    }
    .result {
      width: 100%;
      height: 2em;
      .value {
        font-size: 2em;
      }
    }
    input {
      outline: none;
      width: 100%;
      padding: 5px;
      font-size: 2em;
    }
  }
</style>
