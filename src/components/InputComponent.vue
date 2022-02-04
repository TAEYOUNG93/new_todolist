<template>
  <div class="input_box">
      <input type="text" v-model="currentInput" @keyup.enter="addList">
      <button @click="addList()">add</button>
  </div>
</template>

<script>
export default {
    data() {
        return {
            currentInput: null
        }
    },
    methods: {
        addList() {
            if(this.currentInput !== "") {
                var param =  this.currentInput && this.currentInput.trim();
                this.$emit('addTodo', param);
            }
            this.currentInput = '';
        }
    }
}
</script>

<style scoped>
.input_box {
    border-radius: 30px;
    width: 90%;
    height: 5%;
    display: flex;
    justify-content: center;
    border: 4px solid white;
    padding: 5px;
    margin: 0 auto;
}
.input_box > input {
    width: 80%;
    font-size: 30px;
    font-weight: 700;
    border-style: none;
    background-color: transparent;
    color: rgb(129, 125, 125);
}

input:focus {
    outline: none;
}
</style>