<template>
  <div class="modal" v-if="active">
    <div class="modal__mask">
      <div class="modal__container" v-if="fund">
          <h2>{{ fund.Name }}</h2>
          <h3>Performance history:</h3>
          <LineChart :performance="fund.Performance" />
          <h3>Country allocation:</h3>
          <PieChart :countries="fund.AllocationCountry" />
          <button @click.prevent="active = false" class="modal__button" aria-label="close modal">
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
  .modal {
    &__mask {
      position: fixed;
      z-index: 9998;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, .5);
      display: table;
      transition: opacity .3s ease;
    }    

    &__container {
      position: relative;
      width: 100%;
      max-width: 80vw;
      max-height: 85vh;
      overflow: auto;
      margin: 0px auto;
      padding: 20px 30px;
      background-color: #fff;
      border-radius: 2px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
      transition: all .3s ease;
    }

    &__button {
      width: 40px;
      height: 40px;
      position: absolute;
      top: 10px;
      right: 10px;

      &:before, &:after {
        content:'';
        position:absolute;
        width:36px;
        height:4px;
        background-color: black;
        border-radius:2px;
        top:16px;
        box-shadow:0 0 2px 0 #ccc;
      }

      &:before {
          -webkit-transform:rotate(45deg);
          -moz-transform:rotate(45deg);
          transform:rotate(45deg);
          left:2px;
      }
      &:after {
          -webkit-transform:rotate(-45deg);
          -moz-transform:rotate(-45deg);
          transform:rotate(-45deg);
          right:2px;
      }
    }    
  }
</style>
