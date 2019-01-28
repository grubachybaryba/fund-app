<template>
  <main>
    <section class="u-wrapper">
      <h2>Choose your magnificent fund:</h2>
      <FundList :funds="funds" />
    </section>
    <FundModal />  
  </main>
</template>

<script>
import FundList from './FundList.vue'
import FundModal from '../FundModal/FundModal.vue'

export default {
  name: 'FundPanel',
  components: {
    FundList,
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
