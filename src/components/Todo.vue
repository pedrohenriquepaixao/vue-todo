<template>
  <ul class="list-todo" v-if="todo">
    <li class="list-todo__item" v-bind:class="{ risk: todo.checked }">
      <p class="list-todo__content" v-bind:class="{ riskline: todo.checked }">{{ todo.description }}</p>
      <div class="list-todo__botoes">
        <button class="btn-done" v-bind:class="{ btndone: todo.checked }" @click="$emit('done')">Concluir</button>
        <button class="btn-delete"  @click="$emit('del')">Delete</button>
      </div>
    </li>
  </ul>
</template>
<script>
export default {
  props:{
    todo:{ type: Object, required: true}
  },
}
</script>
<style scoped>
  .list-todo{
    width: 100%;
    list-style: none;
  }

  .list-todo__item{
    color: #181818;
    cursor: pointer;
    padding: 20px 10px;
    display: flex;
    font-weight: bold;
    font-size: 16px;
    justify-content: space-between;
    align-items: center;
  }

  .list-todo__content{
    width: 80%;
    text-align: left;
  }
  .list-todo__botoes{
    width: 30%;
    text-decoration: none;
    display: flex;
  }

  button{
    background-color: none;
    border: none;
    width: 350px;
    height: 50px;
    border-radius: 5px;
    cursor:pointer;
    margin-right: 3px;
    font-weight: bold;
    text-transform: uppercase;
    color: #181818;
  }
  
  .btn-delete{
    background-color: #FF0000;
  }
  .btn-delete:active{
    background-color: #AA0000;
  }

  .btndone{
    border: 1px solid #181818;
  }
  .riskline{
    text-decoration: line-through; 
  }
  .risk{
    background-color: #c1c1c1;
  }
</style>