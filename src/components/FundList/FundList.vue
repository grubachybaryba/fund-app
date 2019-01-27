<template>
  <main>
    <section>
        <h2>Choose your magnificent fund:</h2>
        <ul v-if="funds.length">
          <FundItem v-for="fund in funds" :key="fund._id" :name="fund.value.Name"/>
        </ul>
        <p v-else>
          Ooops, there are no funds!
        </p> 
    </section>
    <FundModal />  
  </main>
</template>

<script>
import FundItem from './FundItem.vue'
import FundModal from '../FundModal/FundModal.vue'

export default {
  name: 'FundList',
  components: {
    FundItem,
    FundModal
  },
  data() {
    return {
      funds: []
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    fetchData: function () {
      fetch('https://api.myjson.com/bins/jpp6w')
        .then(resp => {
          if (resp.ok) {
            return resp.json()
          } else {
            return Promise.reject(resp)
          }
        })
        .then(resp => {
          this.funds = resp
          console.log(resp)
        })
        .catch(error => console.log("An error occured: ", error))
    }
  }  
}
</script>

<style scoped lang="scss">
</style>
