<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addToDo"/>
    <!-- <button v-on:click="addToDo">add</button> -->
    <span class="addContainer" v-on:click="addToDo"><i class="fas fa-plus addBtn"></i></span>
  </div>
</template>

<script>
export default {
  data:function(){
    return {
      newTodoItem:''
    }
  },
  methods:{
    addToDo:function(){
      //localStorage.setItem(키 값, 밸류 값); 
      if(this.newTodoItem != ''){
        var obj = {completed:false,item:this.newTodoItem};
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        
        this.clearInput();
      }
    },
    clearInput:function(){
      this.newTodoItem = '';
    }
  }
}
</script>

<style scoped>
input:focus{outline: none;}
.inputBox{background:#fff; height: 50px;line-height: 50px;border-radius: 5px;}
.inputBox input{border-style: none; font-size: 0.9rem;height: 50px;line-height: 50px;}
.addContainer{float: right;background:linear-gradient(to right, #6478fb,#8763fb);display: block;width: 3rem;border-radius: 0 5px 5px 0;}
.addBtn{color:#fff; vertical-align: middle;}
</style>