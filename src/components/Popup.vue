<template>
  <div>

    <input type="text" v-model="message" />
    <button @click="$emit('closePopup', message)"> [X] close popup </button>
    <h2>popup opened</h2>

  </div>
</template>
<script>


export default {
  name: 'PopupComp',
  emits: {
    closePopup: (message) => {
      // message coming from input event
      if (!message) {
        return false
      } else {
        return true
      }
    }
  },
  data() {
    return {
      message: ''
    }
  }

}
</script>


<style scoped>
input[type=text] {
  width: 10%;
}
</style>