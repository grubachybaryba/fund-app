<template>
  <div class="modal" v-if="active">
    <div class="modal__mask">
      <div class="modal__container" v-if="fund">
          <h2>{{ fund.Name }}</h2>
          <h3>Performance history:</h3>
          <div class="modal__chart">
            <LineChart :performance="fund.Performance" />
          </div>
          <h3>Country allocation:</h3>
          <div class="modal__chart">
            <PieChart :countries="fund.AllocationCountry" />
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
      // position: relative;
      // width: 100%;
      max-width: 100vw;
      max-height: 100vh;
      overflow: auto;
      // margin: 0px auto;
      padding: 20px 30px;
      background-color: #fff;
      // border-radius: 2px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
      transition: all .3s ease;
    }

    &__button {
      @extend %btn-reset;
      font-size: 30px;
      line-height: 30px;
      width: 30px;
      height: 30px;
      color: $c-primary;
      position: absolute;
      top: 10px;
      right: 10px;
      transition: transform 1s ease;
      cursor: pointer;
      
      &:hover {
        transform: rotate(360deg);
      }
    }    
  }
</style>
