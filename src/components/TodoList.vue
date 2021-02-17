<template>
<div class="container col-6">
    <div class="input-group d-flex">
        <input
            class="form-control flex-grow-1"
            type="text"
            placeholder="write todo here"
            v-model="text"
        />
        <input
            class="btn btn-primary btn-sm ml-2"
            type="button"
            value="Add"
            v-on:click="addTodo"
        />
    </div>
        
    <Todo
        v-for="(item, index) in todoList"
        v-bind:todo="item"
        v-bind:key="index"
        v-bind:index="index"
        v-bind:deleteTodo="deleteTodo"
        v-bind:list="todoList"
        v-bind:updateTodo="updateTodo"
    />
</div>
</template>


<script>
import Todo from "./Todo"

export default {
    name: 'TodoList',
    components: {
        Todo
    },

    data: () => ({
        text: '',
        todoList: JSON.parse(localStorage.getItem("TodoList") || "[]")
    }),

    methods: {
        addTodo() {
            if (this.text) {
                this.todoList.push(this.text);
                this.text='';
                localStorage.setItem("TodoList", JSON.stringify(this.todoList));
            }
        },

        deleteTodo(index){
            this.todoList.splice(index,1);
            localStorage.setItem("TodoList", JSON.stringify(this.todoList));
        },

        updateTodo(index,update){
            this.todoList.splice(index,1,update);
            localStorage.setItem("TodoList", JSON.stringify(this.todoList));
        }
    }
}
</script>


<style>

</style>