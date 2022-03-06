<template>
  <div class="calculator-wrapper">
    <div class="row has-justify-content is-multiline has-full-height">
      <div class="column is-12" v-for="(data,key) in calculatorData" :key="key">
        <RangeSlider @calculate="calculate" :settings="data"/>
      </div>
    </div>
  </div>
</template>

<script>
import RangeSlider from '../range-slider/RangeSlider'

export default {
  name: 'Calculator',
  props: {
    calculatorData: {required: true}
  },
  components: {
    RangeSlider,
  },
  data() {
    return {
    }
  },
  methods: {
    calculate(data) {
      this.$emit('calculate', data)
    }
  }
}
</script>

<style lang="scss" src="./Calculator.scss"/>

