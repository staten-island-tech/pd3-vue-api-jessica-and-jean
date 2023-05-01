<template>
  <h1>AP Data</h1>
  <div class="container">
    <SchoolCard
      v-for="schools in schools"
      :key="schools"
      :dbn="schools.dbn"
      :schoolname="schools.schoolname"
      :ap_test_takers_="schools.ap_test_takers_"
      :total_exams_taken="schools.total_exams_taken"
      :number_of_exams_with_scores_3_4_or_5="schools.number_of_exams_with_scores_3_4_or_5"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import SchoolCard from '../components/SchoolCard.vue'
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

h1 {
  text-align: center;
}
</style>
