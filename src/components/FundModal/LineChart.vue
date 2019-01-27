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
        xAxis: {
          categories: []
        },
        series: [{}]
      }
    }
  },
  methods: {
    processData(array) {
      const categories = array.map(obj => {
        return (new Date(obj.Date)).getFullYear().toString()
      })
      const fundValues = array.map(obj => {
        return obj.Value
      })

      this.chartOptions.series = [{ name: 'Performance', data: fundValues }]
      this.chartOptions.xAxis.categories = categories
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
