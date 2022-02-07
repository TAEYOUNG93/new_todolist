<template>
    <div class="container">
        <header-component ></header-component>
        <count-component :todoList="todoList" :completeNumber="completeNumber"></count-component>
        <input-component v-on:addTodo="addTodo"></input-component>
        <list-component :propsdata="todoList" v-on:completeTodos="completeTodos" v-on:removeTodo="removeTodo" ></list-component>
        <footer-component v-on:removeAll="removeAll"></footer-component>
    </div>
</template>

<script>
import CountComponent from '../components/CountComponent.vue'
import FooterComponent from '../components/FooterComponent.vue'
import HeaderComponent from '../components/HeaderComponent.vue'
import InputComponent from '../components/InputComponent.vue'
import ListComponent from '../components/ListComponent.vue'
export default {
    components: {
        HeaderComponent,
        InputComponent,
        ListComponent,
        FooterComponent,
        CountComponent
    },
    data() {
        return {
            todoList: [],
            clear: '',
            completeNumber: [],
        }
    },
    methods: {
        addTodo(params) {
            this.todoList.push(params)
        },
        removeAll(params) {
            this.clear = params;
            this.todoList = [];
            this.completeNumber = [];
        },
        completeTodos(params) {
            this.completeNumber = params
        },
        removeTodo(params) {
            this.todoList.splice(params, 1);
            this.completeNumber.splice(params, 1);
        }

    },

}
</script>

<style scoped>
.container {
    width: 1024px;
    background-size: 1024px 1366px;
    height:1366px;
    background-image: url('../assets/fish.jpg');
    margin: 0 auto;
    padding: 10px;
}



</style>