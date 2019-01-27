<template>
  <highcharts :options="chartOptions"></highcharts>
</template>

<script>
import {Chart} from 'highcharts-vue'

export default {
  name: 'PieChart',
  components: {
    highcharts: Chart 
  },
  props: {
    countries: {
      type: Array,
      required: true
    }
  },  
  data() {
    return {
      chartOptions: {
        chart: {
          plotBackgroundColor: null,
          plotBorderWidth: null,
          plotShadow: false,
          type: 'pie'
        },
        title: {
          text: null
        },
        plotOptions: {
          pie: {
              allowPointSelect: true,
              cursor: 'pointer',
              dataLabels: {
                  enabled: false
              },
              showInLegend: true
          }
        }, 
        series: [{}]
      }
    }
  },
  methods: {
    processData(array) {
      const fundValues = array.map(obj => {
        return {
          name: obj.Key,
          y: obj.Value
        }
      })

      this.chartOptions.series = [{ name: 'Allocation', colorByPoint: true, data: fundValues }]
    }
  },
  watch: { 
    countries: function(newVal) { 
      this.processData(newVal)
    }
  },
  created() {
    this.processData(this.countries)
  }  
}
</script>

<style scoped lang="scss">
</style>
