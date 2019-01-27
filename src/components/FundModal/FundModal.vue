<template>
  <div class="Modal" :class="{ 'is-active': active }">
    <div v-if="fund">
      <h2>{{ fund.Name }}</h2>
      <p>Risk level: {{ fund.RiskLevel }}</p>
      <h3>Performance history:</h3>
      <LineChart :performance="fund.Performance" />
      <h3>Country allocation:</h3>
      <PieChart :countries="fund.AllocationCountry" />
      <button @click.prevent="active = false">Close modal</button>
    </div>
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
  },
  data() {
    return {
      active: false,
      fund: null,
    }
  },
  methods: {
    show() {
      this.active = true;
    }
  },
  created() {
    this.$root.$on('toggleModal', (fund) => {
      this.fund = fund;
      this.show();
    });
  }    
}
</script>

<style scoped lang="scss">
</style>
