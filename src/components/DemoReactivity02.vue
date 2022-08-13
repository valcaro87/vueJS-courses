<template>
  <div>
    <h3>DemoReactivity02</h3>
    <p>{{ superHero.fname }} {{ superHero.lname }} known as {{ superHero.heroName }}</p>
    <p>{{ superHero02.fname2 }} {{ superHero02.lname2 }} known as {{ superHero02.heroName2 }}</p>
    <!-- <p>{{ superHero.fname }} {{ superHero.lname }} known as {{ superHero.heroName }}</p> -->
    <!-- <p>{{ fname }} {{ lname }} known as {{ heroName }}</p> -->

  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'
export default {
  name: 'DemoReactivity02',
  setup() {

    const superHero = reactive({
      fname: 'peter',
      lname: 'parker',
      heroName: 'spiderman'
    })

    const superHero02 = reactive({
      fname2: 'peter2',
      lname2: 'parker2',
      heroName2: 'spiderman2'
    })

    setTimeout(() => {
      superHero.fname = 'clark'
      superHero.lname = 'kent'
      superHero.heroName = 'super-man'
      //console.log(fname)
    }, 4000)


    // return {
    //   superHero,
    //   fname: superHero.fname,
    //   lname: superHero.lname,
    //   heroName: superHero.heroName,

    // }
    return toRefs({ superHero, superHero02 })

  },
  data() {
    return {

    }
  }
}
</script>

<style scoped>
</style>
