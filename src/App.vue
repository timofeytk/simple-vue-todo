<template>
  <div class="header">
    <div class="h1">Список задач</div>
    <form @submit.prevent="addTodo">
      <input 
        type="text" 
        placeholder="Например, купить газету"
        v-model="newTodo"
        />
      <button>Добавить</button>
    </form>
  </div>
  <div class="body">
    <ul>
      <li v-for="todo, index in todos" 
        :key="index">
        <p>{{todo}}</p>
        <span @click="editTodo(index)"><i class="fa-solid fa-pencil"></i></span>
        <span @click="removeTodo(index)"><i class="fa-solid fa-trash"></i></span>
      </li>
    </ul>
  </div>
</template>

<script>
const todos = [
  'купить хлеб',
  'вынести мусор',
  'покормить собаку'
];

export default {
  data(){
    return{
      newTodo: '',
      todos: todos
    }
  },
  methods:{
    addTodo(e){
      e.preventDefault()
      this.todos.push(this.newTodo)
      this.newTodo = ''
    },
    removeTodo(index){
      this.todos.splice(index,1)
    },
    editTodo(index){
      this.newTodo = this.todos[index]
    }
  }
}
</script>

<style>
#app{
  max-width: 800px;
  width: 100%;
  margin: 2em auto;
  border: 1px solid #74c0fc;
  border-radius: 5px;
  padding: 1em;
  color: #333;
}
.header{
  padding: 1em 3em;
}
.body{
  padding: 1em 3em;
}
form{
  display: flex;
}
input{
  border: none;
  border-bottom: 1px solid #74c0fc;
  width: 100%;
  padding-left: 15px;
}
button{
  background-color: #74c0fc;
  border: none;
  color: #fff;
  text-align: center;
  padding: 10px 30px;
  font-size: 14px;
  cursor: pointer;
  outline: none;
}
button:focus{
  outline: none;
  border: none;
}
.h1{
  text-align: center;
  font-size: 24px;
  margin: 1em auto;
}
ul{
  padding-left: 0;
  list-style: none;
}
li{
  display: flex;
  background-color: #74c0fc;
  margin-top: 5px;
  padding: 0 15px;
}
span{
  display: block;
  padding-top: 15px;
  cursor: pointer;
  margin: 0 10px;
}
p{
  width: 100%;
  color: #fff;
}
</style>
