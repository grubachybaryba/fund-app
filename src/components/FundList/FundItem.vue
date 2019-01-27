<template>  
    <li>{{ name }}</li>
</template>

<script>
export default {
  name: 'FundItem',
  props: {
    name: {
      type: String,
      required: true
    }
  }  
}
</script>

<style scoped lang="scss">
</style>
