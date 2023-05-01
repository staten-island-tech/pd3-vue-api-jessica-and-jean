<template>
  <div class="card">
    <h2 class="words">{{ dbn }}</h2>
    <h3 class="words">{{ schoolname }}</h3>
    <h3 class="words">Number of Test Takers:{{ ap_test_takers_ }}</h3>
    <h3 class="words">Total Exams Taken:{{ total_exams_taken }}</h3>
    <h3 class="words">Passing Scores:{{ number_of_exams_with_scores_3_4_or_5 }}</h3>
  </div>
</template>

<script>
import { stringifyQuery } from 'vue-router';

export default {
  name: 'SchoolCard',
  props: {
    dbn: String,
    schoolname: String,
    ap_test_takers_: Number,
    total_exams_taken: Number,
    number_of_exams_with_scores_3_4_or_5: Number
  }
}
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
.words {
  margin-left: 10px;
}
</style>
