<template>
    <div>
        {{todo}} 

        <input type="button" value="delete" v-on:click="deleteTodo"/>

         <input v-if="edit" type="text" v-model="update" placeholder="update me" />
         <input type="button"  value="update" v-on:click="updateTodo"/>
    </div>
</template>


<script>
export default {
    props: {
        todo:  String,
        index: Number,
        list:Array
        
    },
    data(){
        return {
        update:'',
        edit:false
        
        }
    },
    methods: {
         deleteTodo(){
         this.list.splice(this.index,1)
         },
         updateTodo(){
          console.log(this.list)
          if(this.edit){
          
          //this.list[this.index]=this.update
          this.list.splice(this.index,1,this.update)
          this.edit=false}
          else{
          this.edit=true}
          
         }
    }
    
}
</script>


<style>
</style>