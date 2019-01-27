<template>
  <div id="app">
    <AppHeader/>
    <FundList/>
    <FundModal/>
    <AppFooter/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import FundList from './components/FundList/FundList.vue'
import FundModal from './components/FundModal/FundModal.vue'
import AppFooter from './components/AppFooter.vue'


export default {
  name: 'app',
  components: {
    AppHeader,
    FundList,
    FundModal,
    AppFooter
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
