<template>  
    <li>
      <button @click.prevent="toggleModal(fund)">
        {{ fund.Name }}
      </button>
    </li>
</template>

<script>
export default {
  name: 'FundItem',
  props: {
    fund: {
      type: Object,
      required: true
    }
  },
  methods: {
    toggleModal(fund) {
      this.$root.$emit('toggleModal', fund)
    }
  }  
}
</script>

<style scoped lang="scss">
  @import '../../assets/helpers.scss';

  button {
    @extend %btn-reset;
    width: 100%;
    text-align: left;
    padding: $s-sm;
    border-top: 1px solid $c-primary;
    cursor: pointer;
    transition: all .3s ease;

    li:last-child & {
      border-bottom: 1px solid $c-primary;
    }

    &:hover {
      background-color: $c-primary;
      color: #ffffff;
    }
  }  

</style>
