<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ToDoList v-bind:todos="todos" @remove-item="removeToDo"></ToDoList>
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    ToDoList
  },
  data() {
    return {
      todos: [
        { id: 0, text: 'Code' },
        { id: 1, text: 'Test' },
        { id: 2, text: 'Deploy' }
      ]
    }
  },
  methods: {
    removeToDo(id){
      console.log("Removing todo by ID: " + id)

      for(let i = 0; i < this.todos.length; i++){
        if(this.todos[i].id == id) {
          this.todos.splice(i, 1)
        }
      }

    }
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
