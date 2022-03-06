<template>
  <div class="range-slider">
    <div class="row">
      <div class="column pb-2 bold-font">
        {{ settings.text }}
      </div>
      <div class="column is-narrow has-text-right bold-font">
        <span v-if="settings.prefix">{{ settings.prefix }}</span>
        <span>{{ rangeValue }}</span>
        <span v-if="settings.suffix">{{ settings.suffix }}</span>
      </div>
    </div>
    <input style="width: 100%" type="range" @change="changeSliderValue" :value="rangeValue" :min="settings.min" :max="settings.max" :step="settings.step" id="slider" />
  </div>
</template>

<script>
export default {
  name: 'RangeSlider',
  props: {
    settings: {required: true}
  },
  data () {
    return {
      rangeValue: this.settings.value,
    }
  },
  methods: {
    changeSliderValue(value) {
      this.rangeValue = value.target.value
      const emitData = {
        value: this.rangeValue,
        type: this.settings.type
      }
      this.$emit('calculate', emitData)
    }
  }
}
</script>

<style lang="scss" src="./RangeSlider.scss"/>

