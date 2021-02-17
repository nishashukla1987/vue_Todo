<template>
<div class="input-group d-flex mt-2">
    <input v-if="edit" class="form-control flex-grow-1" type="text" v-model="update" placeholder="update me" />
    <span v-else class="flex-grow-1 input-group-text">{{todo}} </span>
    <div class="input-group-append">
        <button class="btn btn-danger" type="button" v-on:click="deleteTodo(index)">Delete</button>
        <button class="btn btn-warning" type="button" v-on:click="editTodoList()">Update</button>
    </div>
</div>
</template>


<script>
export default {
    props: {
        todo:       String,
        index:      Number,
        list:       Array,
        deleteTodo: Function,
        updateTodo: Function
    },

    data() {
        return {
        update:this.todo,
        edit:false        
        }
    },

    methods: {
        editTodoList(){
            if(this.edit){
                this.updateTodo(this.index,this.update)
                this.edit=false
            } else{
                this.edit=true
            }
        }
    }
}
</script>


<style>

</style>