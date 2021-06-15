<template>
  <div id="app">
    <header class="bg-todo">
    </header>
    <div class="container form-todo">
      <form class="" @submit.prevent="addTodo(todo)">
        <h1 class="titulo">To do</h1>
        <div class="input-group">
          <input type="text" class="todo-input" v-model="todo.description"  name="todo" placeholder="Novo To-Do">
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
        
      </form>
      
      <div class="todo-wrapper">
        <Todo v-for="(t,index) in todos" :key="t.id" :todo = "t"  v-on:done="makeDone(index)" v-on:del="del(index)"/>
      </div>

    </div>   
  </div>
</template>

<script>

import Todo from './components/Todo';

export default {
  name: 'App',
  components: { Todo },
  data(){
    return {todos: [],todo: {checked: false}}
  },
  methods: {
      addTodo(todo){
        todo.id = Date.now()
        this.todos.push(todo)
        this.todo = {checked: false}
      },
      makeDone(index){
        this.todos[index].checked = !this.todos[index].checked;
      },
      del(index){
        this.todos.splice(index,1)
      }
  }
}
</script>

<style scoped>
  .bg-todo{
    background-image: linear-gradient(to right,rgba(149, 67, 217,.8),rgba(110, 164, 251,.8)), url("/img/wallpaper.jpg");
    background-position: center;
    background-size: cover;
    width: 100%;
    height: 40vh;
  }

  .titulo{
    text-transform: uppercase;
    color: #F4F4F4;
    font-size: 80px;
    text-align: left;
  }

  .btn{
    background-color: #41B883;
    width: 150px;
    padding: 20px 0;
    border: 0;
    border-radius: 0px 5px 5px 0px;
    text-transform: uppercase;
    color: #F3F3F3;
    font-weight: bold;
    cursor: pointer;
    font-size: 16px;
    transition: all .3s;
  }

  .btn:hover{
    background-color: #41AA83;
  }

  .form-todo{
    z-index: 100;
    transform: translateY(-250px);
  }

  .todo-input{
    width: calc(100% - 150px);
    padding: 20px 10px;
    border: 0;
    border-radius: 5px 0px 0px 5px;
    font-weight: bold;
    margin: 40px 0px;
    font-size: 16px;
  }
  .todo-input:focus,.todo-input:active{
    outline: none;
  }

  .todo-wrapper{
    background-color: #FAFAFA;
    box-shadow: 0px 10px 25px rgba(0,0,0,.2);
    border-radius: 5px; 
    overflow: hidden;
  }
  
</style>
