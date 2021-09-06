<template>
  <div>
    <input type="text" v-model="todoNewItem" placeholder="입력하세요" v-on:keypress.enter="addTodo">
    <span class="addContainer" @click="addTodo">
      <i class= "addBtn fa fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return{
      todoNewItem: ''
    }
  },
  methods: {
    addTodo() {
      if(this.todoNewItem !== ""){
        var value = this.todoNewItem && this.todoNewItem.trim();
        this.$emit('addTodo', value);
        this.clearInput();
      }
    },
    clearInput(){
      this.todoNewItem = '';
    }
  }
}


</script>

<style>
input:focus{
  outline: none;
}

.inputBox{
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}

.inputBox input{
  border-style: none;
  font-size: 0.9rem;
}

.addContainer{
  float: center;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: inline-block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}

.addBtn{
  color: white;
  vertical-align: middle;
}

</style>
