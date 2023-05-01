<template>
  <h1>Passing Scores</h1>
    <div class="chart">
      <Bar v-if="loaded" :data="chartData" :options="chartOptions" />
    </div>
  </template>
  
  <script>
import { Bar } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from 'chart.js'
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
export default {
  name: 'BarChart',
  components: {
    Bar
  },
  props: {
    chartOptions: {
      type: Object,
      required: true,
      default: () => ({
        responsive: true
      })
    },
    chartData: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      loaded: false,
      chartData: {
        labels: ['<20', '21-50', '51-80', '81-100', '101+'],
        datasets: [{ lavel: 'Test Takers In Each School', data: [] }]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: true,
        backgroundColor: ['#9999FF', '#99CCFF', '#CC99FF', '#FF99FF', '#FF99CC']
      }
    }
  },
  async mounted() {
    try {
      const res = await fetch('https://data.cityofnewyork.us/resource/itfs-ms3e.json')
      let data = await res.json()
      const Twenty = data.filter((schools) => schools.number_of_exams_with_scores_3_4_or_5 < 20)
      this.chartData.datasets[0].data.push(Twenty.length)
      const thirtyfifty = data.filter((schools) => (schools.number_of_exams_with_scores_3_4_or_5 > 21) && (schools.number_of_exams_with_scores_3_4_or_5 < 51))
      this.chartData.datasets[0].data.push(thirtyfifty.length)
      const sixtyeighty = data.filter((schools) => (schools.number_of_exams_with_scores_3_4_or_5 > 50 ) && (schools.number_of_exams_with_scores_3_4_or_5 < 81))
      this.chartData.datasets[0].data.push(sixtyeighty.length)
      const ninetyhundred = data.filter((schools) => (schools.number_of_exams_with_scores_3_4_or_5 < 80) && (schools.number_of_exams_with_scores_3_4_or_5 < 101))
      this.chartData.datasets[0].data.push(ninetyhundred.length)
      const overhundred = data.filter((schools) => schools.number_of_exams_with_scores_3_4_or_5 > 100)
      this.chartData.datasets[0].data.push(overhundred.length)
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
    console.log(this.chartData)
  }
}
</script>

<style scoped>
h1 {
  text-align: center;
}

h2 {
  color: #7a6e63;
  font-size: 2rem;
  text-align: center;
}
h2:hover {
  text-decoration: underline;
  transition: 1s;
  color: #7a6e63;
  font-size: 2.5rem;
}
.chart {
  margin-left: 80%;
  flex-wrap: wrap;
  align-self: center;
  margin: 2%;
  height: 500;
  width: 1000px;
}
</style>