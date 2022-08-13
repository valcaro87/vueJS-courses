<template>
  <div>
    <h3>Options - {{ o_fname }}</h3>
    <h3>Options - {{ o_fname }} - {{ o_lname }} - {{ o_heroname }}</h3>
    <h3>Compositions - {{ c_fname }}</h3>
    <h3>Compositions - {{ greet }}</h3>
    <p>Compositions - {{ greetHero }}</p>
    <p>Compositions - reactive - {{ greetHero01 }}</p>
    <p>Compositions - ref - {{ isLoggedIn }}</p>
    <p>Compositions - reactive - {{ isLoggedIn02.value }}</p>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
  name: 'OptionsCompositions',
  setup() {
    const c_fname = ref('peter')
    const c_lname = ref('parker')
    const c_heroname = ref('spiderman')

    c_fname.value = 'kent'
    const greet = `hello ${c_fname.value}`
    const greetHero = `hello ${c_heroname.value} known as ${c_fname.value} ${c_lname.value}`
    //console.log("🚀 ~ setup ~ c_fname", c_fname)

    const hero01 = reactive({
      fname: 'james',
      lname: 'howlett',
      heroName: 'wolverine'
    })
    const greetHero01 = `hello ${hero01.heroName} known as ${hero01.fname} ${hero01.lname}`

    const isLoggedIn = ref(false)
    const isLoggedIn02 = reactive({
      value: false
    })

    return {
      c_fname, // c_fname: c_fname // es6 shorthand 
      greet,
      greetHero,
      greetHero01,
      isLoggedIn,
      isLoggedIn02
    }
  },

  data() {
    return {
      o_fname: 'bruce',
      o_lname: 'wayne',
      o_heroname: 'batman'
    }
  }
}
</script>
<style scoped>
</style>