<template lang="html">
  <GChart
  type="PieChart"
  :data="generationMix"
  :options="chartOptions"
  />
</template>

<script>
import { GChart } from 'vue-google-charts'


export default {
  data () {
    return {
      // Array will be automatically processed with visualization.arrayToDataTable function
      generationMix: [
        ['Fuel', 'Percentage'],
        ['Nuclear', 20.4],
        ['Hydro', 18.9],
        ['Coal', 20.1],
        ['Gas', 13.9]
      ],
      chartOptions: {
        chart: {
          title: 'Company Performance',
          subtitle: 'Sales, Expenses, and Profit: 2014-2017',
        }
      }
    }
  },

  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
</style>
