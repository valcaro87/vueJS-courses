<template>
  <div>
    <input type="text" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
  </div>
</template>



<script>
export default {
  name: 'InputComp',
  props: {
    modelValue: String
  }
}
</script>



<style scoped>
input[type=text] {
  width: 20%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
}
</style>