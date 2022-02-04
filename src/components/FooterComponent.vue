<template>
  <div>
      <button @click="allClear()">All Clear</button>
  </div>
</template>

<script>
export default {
    methods: {
        allClear() {
            this.$emit('removeAll', 'removeAll');
        }
    }
}
</script>

<style>

</style>