<template>
  <div>
    <div class="list_number">
       {{ completeNumber.length }}/{{ todoList.length }}
    </div>
</div>
</template>

<script>
export default {
    props: {
      todoList:Array,
      completeNumber:Array
    },
    data() {
      return {
        // completed: this.completeNumber,
        // listNumber: this.todoList,
      }
    },


}
</script>

<style scoped>
.list_number{
  color: white;
  font-size: 70px;
  font-weight: 500;
  margin-left: 5%;

}

</style>