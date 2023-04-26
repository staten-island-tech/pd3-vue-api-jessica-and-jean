<template>
  <div></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const School = ref('')
async function getSchool() {
  let res = await fetch('https://data.cityofnewyork.us/resource/itfs-ms3e.json')
  let data = await res.json()
  School.value = data
}
onMounted(() => {
  getSchool()
})
</script>

<style scoped></style>
