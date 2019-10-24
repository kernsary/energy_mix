<template lang="html">
  <GChart
  type="PieChart"
  :data="chartData"
  />
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: "chart",
  data() {
    return {
      chartData: this.energyMix
      // chartOptions: {
      //   chart: {
      //     title: 'Company Performance',
      //     subtitle: 'Sales, Expenses, and Profit: 2014-2017',
      //   }
      // }
    }
  },
  props: ["energyMix"],
  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
</style>
