<template>
  <main>
    <section class="u-wrapper">
      <h2>Choose your magnificent fund:</h2>
      <FundList :funds="funds" v-if="!loading" />
      <div class="spinner" v-else>
        <vue-simple-spinner         
        line-fg-color="#ff6468"
        line-size="10" />
      </div>      
    </section>
    <FundModal />  
  </main>
</template>

<script>
import FundList from './FundList.vue'
import FundModal from '../FundModal/FundModal.vue'
import VueSimpleSpinner from 'vue-simple-spinner'

export default {
  name: 'FundPanel',
  components: {
    FundList,
    FundModal,
    VueSimpleSpinner
  },
  data() {
    return {
      loading: false,
      funds: []
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    fetchData: function () {
      this.loading = true
      fetch('https://api.myjson.com/bins/jpp6w')
        .then(resp => {
          this.loading = false
          if (resp.ok) {
            return resp.json()
          } else {
            return Promise.reject(resp)
          }
        })
        .then(resp => {
          this.funds = resp
        })
        .catch(error => console.log("An error occured: ", error))
    }
  }  
}
</script>

<style scoped lang="scss">
  @import '../../assets/helpers.scss';

  .spinner {
    margin: $s-lg;
  }

  main {
    @include media(tablet-portrait-up) {
      padding-bottom: $s-xxl;
    }
  }  
</style>
