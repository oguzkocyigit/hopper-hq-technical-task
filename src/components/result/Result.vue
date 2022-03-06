<template>
  <div class="result-wrapper">
    <div class="row is-multiline">
      <div class="column is-12 mb-4">
        <p class="gray-text fs-2 mb-2">Hours Saved</p>
        <p class="dark-text fs-4 bold-font">{{ hoursSaved }}</p>
      </div>
      <div class="column is-12 mb-4">
        <p class="gray-text fs-2 mb-2">Money Saved</p>
        <p class="dark-text fs-4 bold-font">$ {{ moneySaved }}</p>
      </div>
      <div class="column is-12">
        <button class="fs-2 bold-font">Try Waybook Now</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Result',
  props: {
    hoursSaved: {required: true},
    moneySaved: {required: true}
  }
}
</script>

<style lang="scss" src="./Result.scss"/>

