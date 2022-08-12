<template>
  <div>
    <button @click="incrementCount"> Clicked {{ clickCounter }} times</button>
  </div>
</template>
<script>
import CounterMixin from '../mixins/counter'
export default {
  name: 'ClickCounter',
  mixins: [CounterMixin],
  data() {
    return {
      clickCounter: 99 // component is priority value, not the mixin
    }
  },
  methods: {

  }
}
</script>
<style scoped>
</style>