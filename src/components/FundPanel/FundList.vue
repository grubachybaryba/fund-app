<template>  
  <ul v-if="funds.length">
    <FundItem v-for="fund in funds" :key="fund._id" :fund="fund.value"/>
  </ul>
  <p v-else>
    Ooops, there are no funds!
  </p> 
</template>

<script>
import FundItem from './FundItem.vue'

export default {
  name: 'FundList',
  props: {
    funds: {
      type: Array,
      required: true
    }
  },
  components: {
    FundItem
  },  
}
</script>

<style scoped lang="scss">
  @import '../../assets/helpers.scss';

  ul {
    list-style: none;
    padding: 0;
    margin: ($s-md*1.3) 0 $s-sm 0; 
  }
</style>
