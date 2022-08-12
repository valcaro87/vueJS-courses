<template>
  <div>
    <h2 @mouseover="incrementCount"> hovered: {{ clickCounter }} times</h2>
  </div>
</template>
<script>
import CounterMixin from '@/mixins/counter';
export default {
  name: 'HoverCounter',
  mixins: [CounterMixin],
  data() {
    return {

    }
  },
  methods: {

  }
}
</script>
<style scoped>
</style>