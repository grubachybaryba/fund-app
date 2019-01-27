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
</style>
