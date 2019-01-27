<template>
  <div class="Modal">
      <h2>Fund name</h2>
      <p>Maybe some details</p>
      <h3>Performance history:</h3>
      <LineChart/>
      <h3>Country allocation:</h3>
      <PieChart/>
      <button>Close modal</button>
  </div>
</template>

<script>
import LineChart from './LineChart.vue'
import PieChart from './PieChart.vue'

export default {
  name: 'FundModal',
  components: {
    LineChart,
    PieChart
  }    
}
</script>

<style scoped lang="scss">
</style>
