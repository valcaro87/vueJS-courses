<template>
  <div v-for="(actor, i) in actors" :key="i">
    <slot :actorFname="actor.fname" :actorLname="actor.lname">

    </slot>

  </div>
</template>


<script>
export default {
  name: 'NameListComp',
  data() {
    return {
      actors: [
        {
          fname: 'leo',
          lname: 'the truck'
        },
        {
          fname: 'bli',
          lname: 'ppi'
        }
      ]
    }
  }
}
</script>


<style scoped>
</style>