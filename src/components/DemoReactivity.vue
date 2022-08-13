<template>
  <div>
    <h3>DemoReactivity</h3>
    <p>{{ fname }}</p>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'DemoReactivity',
  setup() {
    const fname = ref('vishwas')

    setTimeout(() => {
      fname.value = 'codeevolution'
      //console.log(fname)
    }, 2000)


    return {
      fname,

    }
  },
  data() {
    return {

    }
  }
}
</script>
<style scoped>
</style>
