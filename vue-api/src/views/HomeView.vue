<template>
  <div></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const scores = ref()
async function getScores() {
  let res = await fetch('https://data.cityofnewyork.us/resource/itfs-ms3e.json')
  let data = await res.json()
  scores.value = data.results
}
onMounted(() => {
  getScores()
})
</script>

<style scoped>
.container {
  width: 80vw;
  margin: 30px auto;
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}
</style>
