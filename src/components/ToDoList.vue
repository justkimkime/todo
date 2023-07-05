<template>
  <div>
    <ul>
      <li v-for="(TodoItem ,index) in propsdata" v-bind:key="TodoItem.key" class="shadow">

        <span class="ckeckBtn" v-bind:class="{checkBtnCompleted:TodoItem.completed}" 
        v-on:click="toggleComplete(TodoItem,index)"><i class="fas fa-check"></i></span>
        <p v-bind:class="{textCompleted:TodoItem.completed}">{{TodoItem.item}}</p>
        <span v-on:click="removeTodo(TodoItem , index)" class="removeBtn"><i class="fa-solid fa-trash-can"></i></span>
        
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  
  props:['propsdata'],
  methods:{
    removeTodo:function(TodoItem, index){
      console.log(TodoItem, index);
      localStorage.removeItem(TodoItem.item);
      this.TodoItems.splice(index,1);
    },
    toggleComplete:function(TodoItem, index){
      console.log(TodoItem,index);
      TodoItem.completed = !TodoItem.completed;
      //로컬스토리지의 데이터를 갱신
      localStorage.removeItem(TodoItem.item);
      localStorage.setItem(TodoItem.item, JSON.stringify(TodoItem));
    }
  }
}
</script>

<style scoped>
ul{list-style:none;padding-left: 0;margin-top: 0;text-align: left;}
li{display: flex;min-height: 50px; height: 50px;line-height: 50px;margin: 0.5rem 0;padding:0 0.9rem;background: #fff;border-radius: 5px;}
li p{margin: 0;;}
.ckeckBtn{line-height: 45px;color:#62acde;margin-right: 15px;}
.checkBtnCompleted{color:#b3adad}
.textCompleted{text-decoration: line-through;color:#b3adad}
.removeBtn{margin-left: auto;color: #de4343;}
</style>