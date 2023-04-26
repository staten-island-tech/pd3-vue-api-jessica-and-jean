<template>
  <div class="card">
    <h2>{{ schools.schoolname }}</h2>
    <h3>{{ id }}</h3>
  </div>
</template>

<script setup>
const props = {
  school: Object,
  id: Number
}
</script>

<style lang="scss" scoped></style>
