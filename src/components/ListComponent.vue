<template>
    <div class="list_container">
        <div  v-for="(todo, index) in propsdata" :key="todo.id">
            <li>
                <v-icon x-large @click="complete(index)" v-if="completeCheckNum.indexOf(index) == -1">mdi-checkbox-outline</v-icon>
                <v-icon x-large @click="completeCencle(index)" v-else> mdi-checkbox-marked</v-icon>
                {{ todo }}
                <v-icon class="remove_icon" x-large @click="removeList(todo)">mdi-close</v-icon>
            </li>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        propsdata: Array
    },
    data() {
        return {
            todos: this.propsdata,
            completeList: [],
            completeCheckNum:[],
        }
    },
    methods: {
        complete(index) {
            if(this.completeList.includes(index) == false) {
                this.completeList.push(index);
                this.completeCheckNum.push(index);
            }
            console.log(index);
            this.$emit('completeTodos', this.completeList)
        },
        completeCencle(index) {
            this.completeCheckNum.splice(this.completeCheckNum.indexOf(index), 1)
            this.completeList.splice(this.completeList.indexOf(index), 1);
        },
        removeList(index) {
            console.log(index);
        }

    },
    computed: {

    }
}
</script>

<style scoped>

.list_container {
    border-radius: 10px;
    color: black;
    background-color: rgba(48, 47, 43, 0.116);
    margin: 5%;
    min-height: 70%;
    padding-top: 3%;

}
li {
    margin-left: 5%;
    margin-bottom: 6%;
    list-style: none;
    font-size: 30px;
    font-weight: bold;
    color: rgb(51, 46, 46);
}

li > .remove_icon {
    float: right;
    margin-right: 5%;
}


</style>