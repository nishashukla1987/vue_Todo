<template>
    <div>
        <input type="text" placeholder="write todo here" v-model="text"/>
        <input type="button" value="Add" v-on:click="addTodo"/>
        
        <div>            
            <Todo
                v-for="(item, index) in todoList"
                v-bind:todo="item"
                v-bind:key="index"
                v-bind:index="index"
                v-bind:list="todoList"
            />
        </div>
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
        todoList: []
    }),
    methods: {
        addTodo() {
            this.todoList.push(this.text);
        }
    }
}
</script>


<style>
</style>