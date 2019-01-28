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

  // global styles
  #app {
    font-family: 'Exo', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: $c-secondary;
  }

  // wrapper global utility class
  .u-wrapper {
    padding: $s-md;

    @include media(tablet-portrait-up) {
      padding: $s-md $s-lg;
    }

    @include media(tablet-landscape-up) {
      max-width: $wrapper-width;
      margin: 0 auto;
      padding: $s-md 0;
    }

    @include media(desktop-up) {
      padding: ($s-md*1.2) 0;
    }
  }
</style>
