<template>
  <h1>Test Takers</h1>
  <div class="chart2">
    <Pie v-if="loaded" :options="chartOptions" :data="chartData" />
  </div>
</template>

<script>
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'
import { Doughnut } from 'vue-chartjs'
ChartJS.register(ArcElement, Tooltip, Legend)
export default {
  name: 'PieChart',
  components: {
    Doughnut
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
        labels: ['<20', '20-50', '51-80', '81-100', '101-130', '131-150', '151-180', '181+'],
        datasets: [{ data: [] }]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: true,
        backgroundColor: [
          '#FFFFCC',
          '#E5FFCC',
          '#CCFFCC',
          '#CCFFE5',
          '#CCFFFF',
          '#CCE5FF',
          '#CCCCFF',
          '#E5CCFF'
        ]
      }
    }
  },
  async mounted() {
    try {
      const res = await fetch('https://data.cityofnewyork.us/resource/itfs-ms3e.json')
      let data = await res.json()
      const one = data.filter((schools) => schools.ap_test_takers_ < 20)
      this.chartData.datasets[0].data.push(one.length)
      const two = data.filter(
        (schools) => schools.ap_test_takers_ > 19 && schools.ap_test_takers_ < 51
      )
      this.chartData.datasets[0].data.push(two.length)
      const three = data.filter(
        (schools) => schools.ap_test_takers_ > 51 && schools.ap_test_takers_ < 81
      )
      this.chartData.datasets[0].data.push(three.length)
      const four = data.filter(
        (schools) => schools.ap_test_takers_ < 80 && schools.ap_test_takers_ < 101
      )
      this.chartData.datasets[0].data.push(four.length)
      const five = data.filter(
        (schools) => schools.ap_test_takers_ < 100 && schools.ap_test_takers_ < 131
      )
      this.chartData.datasets[0].data.push(five.length)
      const six = data.filter(
        (schools) => schools.ap_test_takers_ < 130 && schools.ap_test_takers_ < 151
      )
      this.chartData.datasets[0].data.push(six.length)
      const seven = data.filter(
        (schools) => schools.ap_test_takers_ < 150 && schools.ap_test_takers_ < 181
      )
      this.chartData.datasets[0].data.push(seven.length)
      const eight = data.filter((schools) => schools.ap_test_takers_ > 181)
      this.chartData.datasets[0].data.push(eight.length)
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
.chart2 {
  margin-left: 80%;
  flex-wrap: wrap;
  justify-content: center;
  display: flex;
  margin: 2%;
  height: 1000px;
  width: 1000px;
}
</style>
