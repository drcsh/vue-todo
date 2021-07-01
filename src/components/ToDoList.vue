<template>
<div id="todo-list-app">
  <h1>Todo:</h1>
  <ul>
    <ToDoItem
        v-for="item in todos"
        :key="item.id"
        :item="item"
        @remove-item="removeListener"
    ></ToDoItem>
  </ul>
</div>
</template>

<script>
import ToDoItem from "@/components/ToDoItem";
export default {
  name: "ToDoList",
  components: {ToDoItem},
  props: ['todos'],
  emits: ['remove-item'],
  methods:{
      removeListener(id) {
        // Re-emit the event for the parent to handle
        this.$emit('remove-item', id);
      }
    }
}
</script>

<style scoped>

</style>