<template>
  <div id="app">
    <ToDoHeader></ToDoHeader>
    <ToDoInput v-on:="addOneItem"></ToDoInput>
    <ToDoList v-bind:propsdata="TodoItems"></ToDoList>
    <ToDoFooter></ToDoFooter>
  </div>
</template>

<script>

import ToDoHeader from './components/ToDoHeader.vue';
import ToDoInput from './components/ToDoInput.vue';
import ToDoList from './components/ToDoList.vue';
import ToDoFooter from './components/ToDoFooter.vue';


export default {
  data:function(){
    return {
      TodoItems:[]
    }
  },
  methods:{
    addOneItem:function(){

    }

  },
  created:function(){
    if(localStorage.length > 0){
      for(var i = 0; i < localStorage.length; i ++){
       this.TodoItems.push( JSON.parse(localStorage.getItem(localStorage.key(i))));
        //this.TodoItems.push(localStorage.key(i))
      }
    }
  },
  components:{
    'ToDoHeader':ToDoHeader,
    'ToDoInput':ToDoInput,
    'ToDoList':ToDoList,
    'ToDoFooter':ToDoFooter,
  }
}
</script>

<style>
body{text-align: center; background-color:#f6f6f6;}
input{border-style: none; width:calc(100% - 3rem);float:left;box-sizing: border-box; }
button{border-style: groove;}
.shadow{box-shadow:5px 10px 10px rgba(0,0,0,0.03)}
</style>
