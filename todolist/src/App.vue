<template>
  <div id="app">
    <todoHeader></todoHeader>
    <todoInput v-on:addTodo="addTodo"></todoInput>
    <todoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></todoList>
    <todoFooter v-on:removeAll="clearAll"></todoFooter>
  </div>
</template>

<script>
import todoHeader from './components/todoHeader';
import todoInput  from './components/todoInput';
import todoList   from './components/todoList';
import todoFooter from './components/todoFooter';

export default{
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    //추가
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    //삭제
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem, index);
      this.todoItems.splice(index,1);
    },
    //전체 삭제
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    }
  },
  components: {
    'todoHeader': todoHeader,
    'todoInput': todoInput,
    'todoList': todoList,
    'todoFooter': todoFooter
  }
}

</script>

<style>
body{
  text-align : center;
  background-color: #F6F6F8;
}

input{
  border-style: groove;
  width: 200px;
}

button{
  border-style: groove;
}

.shadow{
  box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
}


</style>
