<template>
<div class=" container col-6" >
    <div class="input-group d-flex">
        <input  class="form-control flex-grow-1" type="text" placeholder="write todo here" v-model="text"/>
        <input class="btn btn-primary btn-sm ml-2" type="button" value="Add" v-on:click="addTodo" />
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
        todoList: [],
      
    }),
    methods: {
        addTodo() {
            this.todoList.push(this.text);
            this.text=''
        },
          deleteTodo(index){
         this.todoList.splice(index,1)
         
        },
          updateTodo(index,update){
          console.log(update);
          
          
          
          this.todoList.splice(index,1,update)
          
    }
}
}
</script>


<style>

</style>