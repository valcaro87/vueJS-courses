<template>
  <hr>
  <div>
    <h1>Component C</h1>
  </div>

  <EeeComp />
</template>


<script>
import EeeComp from './Eee.vue'

export default {
  name: 'CccComp',
  components: {
    EeeComp,
  },

}
</script>
<style scoped>
</style>