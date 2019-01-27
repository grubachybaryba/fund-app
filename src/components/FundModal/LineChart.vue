<template>
  <div>
    <highcharts :options="chartOptions"></highcharts>
  </div>
</template>

<script>
import {Chart} from 'highcharts-vue'

export default {
  name: 'LineChart',
  components: {
    highcharts: Chart 
  },
  props: {
    performance: {
      type: Array,
      required: true
    }
  },  
  data() {
    return {
      chartOptions: {
        chart: {
          type: 'spline'
        },
        title: {
          text: null
        },
        legend: {
          enabled: false,
        },
        series: [{}]
      }
    }
  },
  methods: {
    processData(array) {
      const processedData = array.map(obj => Object.values(obj).reverse())      
      this.chartOptions.series = [{ data: processedData }]
    }
  },
  watch: { 
    performance: function(newVal) { 
      this.processData(newVal)
    }
  },
  created() {
    this.processData(this.performance)
  }  
}
</script>

<style scoped lang="scss">
</style>
