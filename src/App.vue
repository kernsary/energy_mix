<template lang="html">
  <div class="">
    <h1>Energy Mix</h1>
    <p>from {{startTime}} to {{endTime}}</p>
    <chart :energyMix="energyMix"></chart>
  </div>
</template>

<script>
import Chart from './components/Chart.vue'

export default {
  data() {
    return {
      startTime: "",
      endTime: "",
      energyMix: [
        ["Fuel", "Percentage"]
      ],
      chartOptions: {
        chart: {
          title: 'Company Performance',
          subtitle: 'Sales, Expenses, and Profit: 2014-2017',
        }
      }
    }
  },
  methods: {
    fetchData(){
      fetch('https://api.carbonintensity.org.uk/generation')
      .then(res => res.json())
      .then((responseData) => {
        this.transformData(responseData.data.generationmix);
        this.startTime = responseData.data.from;
        this.endTime = responseData.data.to
      })
    },

    transformData(arr) {
      for (var i = 0; i < arr.length; i++) {
        const sub_array = [arr[i].fuel, arr[i].perc];
        this.energyMix.push(sub_array);
      }
    }
  },
  components: {
    "chart": Chart
  },
  mounted(){
    this.fetchData();
  }
}
</script>

<style lang="css" scoped>
</style>
