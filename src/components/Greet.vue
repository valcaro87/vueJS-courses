<template>
  <div>
    <h1>hellow {{ moreName }} - {{ heroName }}</h1>
  </div>
</template>



<script>
export default {
  name: 'GreetComp',
  props: ['moreName', 'heroName']
}
</script>

<style scoped>
</style>