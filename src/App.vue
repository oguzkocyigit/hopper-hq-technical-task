<template>
  <div class="home-view">
    <div class="column is-8 is-offset-2 is-10-tablet is-offset-tablet-1 is-12-mobile is-offset-mobile-0">
      <div class="row is-mobile is-multiline">
        <div class="column is-12 has-text-centered">
          <h1 class="fs-5 mb-4">Calculate your Waybook ROI</h1>
          <p class="has-gray-text mb-5">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et
            dolore
            magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
            commodo
            consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
            pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
            est
            laborum.
          </p>
        </div>
        <div class="column is-8 is-12-mobile">
          <Calculator @calculate="updateResult" :calculator-data="calculatorData"/>
        </div>
        <div class="column is-4 is-12-mobile">
          <Result :money-saved="moneySaved" :hours-saved="hoursSaved"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Calculator from './components/calculator/Calculator'
import Result from './components/result/Result'

export default {
  name: 'App',
  components: {
    Calculator,
    Result
  },
  data() {
    return {
      calculatorData: [
        {
          text: 'What is your avarage manager salary?',
          value: 100,
          prefix: '$',
          suffix: 'K',
          step: 10,
          min: 50,
          max: 500,
          type: 'salary',
        },
        {
          text: 'How many people will you hire this year?',
          value: 4,
          step: 1,
          min: 0,
          max: 50,
          type: 'people'
        },

        {
          text: 'How many weeks does it take to get a new hire upto speed?',
          value: 3,
          step: 1,
          min: 0,
          max: 52,
          type: 'time'
        },
      ]
    }
  },
  computed: {
    hoursSaved() {
      return (this.calculatorData.find((item) => item.type === 'time').value * 45) * (this.calculatorData.find((item) => item.type === 'people').value)
    },
    moneySaved() {
      return (this.calculatorData.find((item) => item.type === 'salary').value) * (this.calculatorData.find((item) => item.type === 'time').value * 45) * (this.calculatorData.find((item) => item.type === 'people').value)
    }
  },
  methods: {
    updateResult(data) {
      this.calculatorData.find((item) => item.type === data.type).value = data.value
    }
  }
}
</script>
