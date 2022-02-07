<template>
    <div class="list_container">
        <div  v-for="(todo, index) in propsdata" :key="todo.id">
            <li>
                <v-icon x-large @click="complete(index)" v-if="completeCheckNum.indexOf(index) == -1">mdi-checkbox-outline</v-icon>
                <v-icon x-large @click="completeCencle(index)" v-else> mdi-checkbox-marked</v-icon>
                <div v-if="modify" id="list_style" :class="{active: getActive() === index}">
                    {{ todo }}
                </div>
                <div v-else class="list_style">
                    <input type="text">
                </div>
                <v-icon x-large class="remove_icon" @click="removeTodo(index)">mdi-close</v-icon>
                <v-icon x-large class="pancil_icon" @click="modifyTodo(index)">mdi-pencil</v-icon>
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
            todo: 0,
            completeList: [],
            completeCheckNum:[],
            isActive: false,
            modify: true,
        }
    },
    methods: {
        complete(index) {
            // console.log('complete = ' + index);
            if(this.completeList.includes(index) == false) {
                this.completeList.push(index);
                this.completeCheckNum.push(index);
            }
            this.$emit('completeTodos', this.completeList)
            this.getActive(index);

        },
        completeCencle(index) {
            this.completeCheckNum.splice(this.completeCheckNum.indexOf(index), 1)
            this.completeList.splice(this.completeList.indexOf(index), 1);
            // this.getActive(0);
        },
        removeTodo(index) {
            this.$emit('removeTodo', index)
        },
        getActive(params) {
            console.log('todoIndex = ' + params);
        },
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
    margin-bottom: 2%;
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

li > .pancil_icon {
    margin-right: 5%;
    float: right;
}

li > .remove_icon {
    float: right;
    margin-right: 5%;
}

#list_style {
    margin-left: 2%;
    display: inline-block
}

.active {
    text-decoration: line-through
}


</style>