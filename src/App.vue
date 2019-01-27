<template>
  <div id="app">
    <AppHeader/>
    <FundPanel/>
    <AppFooter/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import FundPanel from './components/FundPanel/FundPanel.vue'
import AppFooter from './components/AppFooter.vue'

export default {
  name: 'app',
  components: {
    AppHeader,
    FundPanel,
    AppFooter
  }
}
</script>

<style lang="scss">
@import './assets/helpers.scss';

#app {
  font-family: 'Exo', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
