<template>
  <div class="card">
    <h2>{{ schools.schoolname }}</h2>
    <h3>{{ id }}</h3>
  </div>
</template>

<script setup>
const props = defineprops({
  school: Object,
  id: Number
})
</script>

<style>
.card {
  width: 28%;
  height: 500px;
  background-color: aliceblue;
  margin: 30px 0;
  display: flex;
  flex-direction: column;
}
</style>
