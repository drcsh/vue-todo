<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ToDoList v-bind:todos="todos" @remove-item="removeToDo"></ToDoList>
    <NewToDoForm @new-todo="addToDo"></NewToDoForm>
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue'
import NewToDoForm from "@/components/NewToDoForm";
export default {
  name: 'App',
  components: {
    ToDoList,
    NewToDoForm
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
    /**
     * Removes a ToDo item by ID
     * @param {number} id: id to delete
     */
    removeToDo(id) {
      console.log("Removing todo by ID: " + id)

      for(let i = 0; i < this.todos.length; i++){
        if(this.todos[i].id == id) {
          this.todos.splice(i, 1)
        }
      }

    },
    /**
     * Add a new ToDo to the todo list.
     * @type {string} input: text for the new ToDo
     */
    addToDo(input) {
      // First find the highest Id in the list - this would usually
      // be a pk in the DB and handled by the DB.
      let highestId = 0;
      for (let i = 0; i < this.todos.length; i++) {
        if (this.todos[i].id > highestId){
          highestId = this.todos[i].id
        }
      }
      this.todos.push({
        id: highestId + 1,
        text: input
      })
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
