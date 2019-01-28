<template>
  <header class="header">
    <div class="u-wrapper">
      <h1>fund app</h1>
      <p>the best investment app in the entire universe</p>
    </div>
  </header>
</template>

<script>
export default {
  name: 'AppHeader'  
}
</script>

<style scoped lang="scss">
  @import '../assets/helpers.scss';

  .header {
    background: url("../assets/patch.png"), 
    linear-gradient(135deg,
     rgba(16, 24, 30, 0.9) 0%, 
     rgba(16, 24, 30, 0.91) 7%,
     rgba(183, 71, 88, 0.95) 46%, 
     rgba(235, 109, 101, 0.95) 62%, 
     rgba(255, 130, 81, 0.9) 75%,
     rgba(255, 168, 29, 0.9) 100%);
    min-height: 250px;
    color: #ffffff;    
  }

  h1 {
    font-size: 60px;
    font-weight: 900;
    margin: $s-lg 0 $s-xs 0;    
  }

  p {
    font-size: 24px;
    margin: $s-sm 0 $s-xs 0;
  }
</style>
