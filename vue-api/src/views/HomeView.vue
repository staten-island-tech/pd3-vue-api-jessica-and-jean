<template>
  <div></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import ScoresCard from '../components/ScoresCard.vue'
const schools = ref('')

async function getApData() {
  let res = await fetch('https://data.cityofnewyork.us/resource/itfs-ms3e.json')
  let data = await res.json()
  schools.value = data
}

onMounted(() => {
  getApData()
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
