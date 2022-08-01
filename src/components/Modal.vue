<template>
  <!-- <div class="modal-overlay" @click="$emit('closeModal')"> -->
  <div class="modal-overlay">
    <div class="modal-content">
      <slot></slot>
      <hr />
      <button @click="$emit('closeModal')">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalComp',
  emits: ['closeModal'],
};
</script>

<style>
.modal-overlay {
  z-index: 1;
  /* position: absolute; */
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: grid;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.4);
  width: 100vw;
  height: 100vh;
}

.modal-content {
  font-family: "Fondamento", cursive;
  padding: 20px;
  background: #fff;
  border-radius: 2px;
  display: inline-block;
  min-height: 300px;
  margin: 1rem;
  position: relative;
  min-width: 300px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  justify-self: center;
}
</style>