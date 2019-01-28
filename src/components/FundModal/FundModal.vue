<template>
  <div class="modal" v-if="active">
    <div class="modal__mask">
      <div class="modal__container" v-if="fund">
          <h2>{{ fund.Name }}</h2>
          <div class="modal__chartWrap">
            <div class="modal__chart">
              <h3>Performance history:</h3>
              <LineChart :performance="fund.Performance" />
            </div>          
            <div class="modal__chart">
              <h3>Country allocation:</h3>
              <PieChart :countries="fund.AllocationCountry" />
            </div>
          </div>        
        <button @click.prevent="active = false" class="modal__button" aria-label="close modal">
          &#10006;
        </button>
      </div>        
    </div>    
  </div>
</template>

<script>
import LineChart from './LineChart.vue'
import PieChart from './PieChart.vue'

export default {
  name: 'FundModal',
  components: {
    LineChart,
    PieChart
  },
  data() {
    return {
      active: false,
      fund: null,
    }
  },
  methods: {
    show() {
      this.active = true;
    }
  },
  created() {
    this.$root.$on('toggleModal', (fund) => {
      this.fund = fund;
      this.show();
    });
  }    
}
</script>

<style scoped lang="scss">
  @import '../../assets/helpers.scss';

  .modal {
    &__mask {
      position: fixed;
      z-index: 9998;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, .5);
    }    

    &__container {
      max-width: 100vw;
      max-height: 100vh;
      overflow: auto;
      padding: $s-md;
      background-color: #ffffff;
      box-shadow: 0 50vh 0 50vh #ffffff; // extending element to the bottom of the page if needed  
      transition: all .3s ease;

      @include media(tablet-portrait-up) {
        padding: ($s-lg*0.8) $s-lg;
      }

      @include media(desktop-up) {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        max-width: 1100px;
        max-height: 85vh;
        border-radius: 2px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
      }
    }

    &__chartWrap {
      margin-top: $s-md;
      @include media(desktop-up) {
        display: flex;
      }
    }

    &__chart {
      margin: $s-md 0;

      @include media(tablet-portrait-up) {
        margin: $s-lg 0 $s-xl;
      }

      @include media(desktop-up) {
        margin: 0 0 $s-md 0;
        flex-grow: 1;
      }
    }

    h3 {
      @include media(desktop-up) {
        margin-bottom: $s-lg;
      }
    }

    &__button {
      @extend %btn-reset;
      font-size: 30px;
      line-height: 30px;
      width: 40px;
      height: 40px;
      color: $c-primary;
      position: absolute;
      top: ($s-xs*0.5);
      right: ($s-xs*0.5);
      transition: transform 1s ease;
      cursor: pointer;
      
      &:hover {
        transform: rotate(360deg);
      }

      &:focus {
        outline: none;
        border: 1px dashed $c-primary;
        border-radius: 50%;
      }

      @include media(tablet-portrait-up) {
        top: $s-md;
        right: $s-md;
      }
    }    
  }
</style>
