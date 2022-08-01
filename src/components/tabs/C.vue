<template>
  <div>
    <h4>Tab C</h4>
    <div>Pack my box with five dozen liquor jugs.</div>
    <input type="text" v-model="quizA">
    {{ quizA }}
  </div>
</template>


<script>
export default {
  name: 'TabC',
  data() {
    return {
      quizA: '',
    }
  }
}
</script>


<style scoped>
</style>