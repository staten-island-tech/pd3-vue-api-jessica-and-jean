<template>
  <div class="container">
    <ScoresCard
      v-for="(HighScore, index) in scores"
      :key="HighScore.number_of_exams_with_scores_3_4_or_5"
      :id="index + 1"
      :scores="HighScore"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import ScoresCard from '../components/ScoresCard.vue'
const scores = ref('')
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
