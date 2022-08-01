<template>
  <div>
    <slot></slot>
    <h4>Component styles are applied globally, (by applying 'scoped' only apply to component)</h4>

  </div>
</template>
<script>


export default {
  name: 'ChildStyles'
}
</script>


<style scoped>
h4 {
  color: orangered;
}
</style>