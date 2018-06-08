<template>
  <circle v-bind:cx="position[0]" v-bind:cy="position[1]" :r="radius"/>
</template>

<script>

export default {
  name: 'Food',
  props: {
    position: {
      type: Array
    },
    radius: {
      default: 10,
      type: Number
    }
  }
}
</script>

<style scoped>
</style>
