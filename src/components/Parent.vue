<template>
  <div>
    <h2>Parent Component</h2>
    <button @click="showChild = !showChild">Toggle Child</button>
    <!--  the child / unmounting phase -->
    {{ showChild }}
    <ChildComp v-if="showChild" />

  </div>
</template>
<script>
import ChildComp from './Child.vue'

export default {
  name: 'ParentComp',
  components: {
    ChildComp,
  },
  data() {
    return {
      showChild: true,
    }
  },
  beforeCreate() {
    console.log(" parent  beforeCreate")
  },
  created() {
    console.log(" parent  created")
  },
  beforeMount() {
    console.log(" parent  beforeMount")
  },
  mounted() {
    console.log(" parent  mounted")
  },
  beforeUpdate() {
    console.log(" parent  beforeUpdate")
  },
  updated() {
    console.log(" parent  updated")
  },
  beforeUnmount() {
    console.log(" parent  beforeUnmount")
  },
  unmounted() {
    console.log(" parent  unmounted")
  },
}
</script>
<style scoped>
</style>