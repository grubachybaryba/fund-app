<template>
  <section>
      <h2>Choose your magnificent fund:</h2>
      <ul>
          <FundItem/>
      </ul>
  </section>
</template>

<script>
import FundItem from './FundItem.vue'

export default {
  name: 'FundList',
  components: {
    FundItem
  }  
}
</script>

<style scoped lang="scss">
</style>
