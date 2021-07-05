<template>
<div class="new-todo">
  <form id="new-todo-form" class="form-inline" novalidate @submit.prevent="newToDo">
    <NewToDoInput v-bind:inputName="formInputName"></NewToDoInput>
    <button type="submit" class="add">Add</button>
  </form>
</div>

</template>

<script>
import NewToDoInput from "@/components/Inputs/NewTodoInput";
export default {
  name: "NewToDoForm",
  components: {NewToDoInput},
  data() {
    return {
      formInputName: 'newToDoInput'
    }
  },
  methods: {
    /**
     * Handles the button press for adding a ToDo - finds the
     * input element in the form, reads the input, trims it, and
     * if it's not blank, emits a new-todo event.
     * @param submitEvent
     */
    newToDo(submitEvent){
      console.log(submitEvent)
      let new_item = ""

      for (let element of submitEvent.target.elements){
        if (element.name == this.formInputName) {
          new_item = element.value.trim()
          break
        }
      }

      if (new_item != ""){
        this.$emit('new-todo', new_item)
      } else {
        console.log("Empty todo - doing nothing")
      }

    }
  }
}
</script>

<style scoped>
  .form-inline {
    display: inline-flex;
    flex-flow: row wrap;
    align-items: center;
    font-family: Roboto, sans-serif;
  }
  .add {
    background-color: #42b983;
    display:inline-block;
    padding:0.3em 1.2em;
    margin-left: 0.5em;
    border:0.16em solid rgba(255,255,255,0);
    border-radius:2em;
    box-sizing: border-box;
    text-decoration:none;
    font-family:'Roboto',sans-serif;
    font-weight:300;
    color:#FFFFFF;
    text-align:center;
    transition: all 0.2s;
  }
  .add:hover {
    background-color:#4eb5f1;
  }
</style>