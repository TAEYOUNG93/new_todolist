<template>
  <div>
      <v-icon x-large class="all_clear" @click="allClear()">mdi-trash-can</v-icon>
      <!-- <button @click="allClear()">All Clear</button> -->
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

<style scoped>
.all_clear {
    margin-left: 5%;
    margin-bottom: 10%;
}

</style>