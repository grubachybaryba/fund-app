<template>
  <footer class="footer">
    <div class="u-wrapper">
      <p>Made with &#9829; in Białystok, Poland</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter'  
}
</script>

<style scoped lang="scss">
  @import '../assets/helpers.scss';

  .footer {
    background-color: $c-secondary;
    color: #ffffff;    

    @include media(tablet-portrait-up) {
      position: fixed;
      bottom: 0;
      width: 100%;
    }
  }

  p {
    margin: 0;
  }

</style>
