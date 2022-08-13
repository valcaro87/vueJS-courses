<template>
  <div>
    <h3>{{ fname }}</h3>
    <input type="text" ref="myInput" v-model="fnamelname">
    <button @click="changeName(fnamelname)"> Change name</button>

    <h4>{{ count }}</h4>
    <button @click="incrementCount"> ++++ </button>

    <p>{{ fname }} {{ lname }} </p>
    <p>new name: {{ newname }} </p>

  </div>
</template>
<script>
import { ref, reactive, toRefs } from 'vue'
export default {
  name: 'ReplacingMethods',
  setup() {
    const count = ref(0)
    const state = reactive({
      fname: 'peter',
      lname: 'parker',
      newname: ''
    })

    // let inputValue1 = ref('')

    function incrementCount() {
      count.value++
    }

    function changeName(fnamelname) {
      state.fname = 'clark'
      state.lname = 'kent'
      state.newname = fnamelname
    }

    function getInputValue() {
      // return $refs.myInput.value
      return 'wla lang'
    }

    return {
      count,
      incrementCount,
      changeName,
      getInputValue,
      ...toRefs(state)
    }
  },
  // data() {
  //   return {
  //     fname: ''
  //   }
  // },
  // methods: {
  //   changeName(fname) {
  //     this.fname = fname
  //   },
  //   getInputValue() {
  //     return this.$refs.myInput.value
  //   }
  // }
}
</script>
<style scoped>
</style>
