<template>
  <div>
    <ul>
      <li v-for="(TodoItem ,index) in TodoItems" v-bind:key="TodoItem" class="shadow">
        <p>{{TodoItem}}</p>
        <span v-on:click="removeTodo(TodoItem , index)" class="removeBtn"><i class="fa-solid fa-trash-can"></i></span>
        
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data:function(){
    return {
      TodoItems:[]
    }
  },
  created:function(){
    if(localStorage.length > 0){
      for(var i = 0; i < localStorage.length; i ++){
        this.TodoItems.push(localStorage.key(i))
      }
    }
  },
  methods:{
    removeTodo:function(TodoItem, index){
      console.log(TodoItem, index);
      localStorage.removeItem(TodoItem);
      this.TodoItems.splice(index,1);
    }
  }
}
</script>

<style>
ul{list-style:none;padding-left: 0;margin-top: 0;text-align: left;}
li{display: flex;min-height: 50px; height: 50px;line-height: 50px;margin: 0.5rem 0;padding:0 0.9rem;background: #fff;border-radius: 5px;}
li p{margin: 0;;}
.ckeckBtn{line-height: 45px;color:#62acde;margin-right: 5px;}
.checkBtnCompleted{color:#b3adad}
.textCompleted{text-decoration: line-through;color:#b3adad}
.removeBtn{margin-left: auto;color: #de4343;}
</style>