<template>
  <hr>
  <div>
    <h1>Component F</h1>
    <h3>Provide and Inject</h3>
    <div> username: {{ username }} </div>
  </div>
</template>


<script>
export default {
  name: 'FffComp',
  inject: ['username'] // coming from App component provide()
}
</script>


<style scoped>
</style>