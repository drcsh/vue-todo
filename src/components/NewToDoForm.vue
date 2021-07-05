<template>
<div class="new-todo">
  <form id="new-todo-form" novalidate @submit.prevent="newToDo">
    <NewToDoInput v-bind:inputName="formInputName"></NewToDoInput>
    <button type="submit">Add</button>
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

</style>