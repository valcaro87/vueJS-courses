<template>

  <div class="card" v-for="(employee, i) in employees" :key="i">
    <div id="card-header">
      <slot name="header">

      </slot>
    </div>

    <slot name="image">
      <!-- any html passed from parent component will be displayed here -->
    </slot>

    <div class="card-container">
      <h4><b>{{ employee.name }}</b></h4>
      <p>{{ employee.title }}</p>
    </div>

    <div id="card-footer">
      <slot name="footer">

      </slot>
    </div>

  </div>
</template>


<script>
export default {
  name: "CardComp",
  props: ['employees']
}
</script>


<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  width: 10%;
  margin: 0 auto;
  display: inline-block;
  margin: 0px 10px;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

.card-container {
  padding: 2px 16px;
}
</style>