<template>
  <div class="card">
    <h2>{{ scores.schoolname }}</h2>
    <h3>{{ id }}</h3>
  </div>
</template>

<script setup>
const props = {
  scores: object,
  id: number,
  ap_test_takers_: number,
  total_exams_taken: number,
  number_of_exams_with_scores_3_4_or_5: number
}
</script>

<style lang="scss" scoped></style>
