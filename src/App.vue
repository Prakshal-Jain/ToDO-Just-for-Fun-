<template>
  <div id="app">
    <AddToDo v-bind:numbers="todos.length" v-on:new_todo="handleNewTodo" />
    <Todos v-bind:todos="todos" v-on:delete="handleDelete"/>
  </div>
</template>

<script>
import Todos from './components/todos'
import AddToDo from './components/AddTodo'
export default {
  name: 'App',
  components: {
    Todos,
    AddToDo
  },
  data(){
    return{
      todos: []
    }
  },
  methods:{
    handleDelete(id){
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    handleNewTodo(todo){
      console.log(todo)
      this.todos = [...this.todos,todo]
    }
  },
  created(){
    fetch('http://jsonplaceholder.typicode.com/todos?_limit=8')
    .then(response => response.json())
    .then(info => this.todos = info)
    .catch(err => console.log(err))
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
