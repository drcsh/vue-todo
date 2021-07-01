<template>
<div id="todo-list-app">
  <h1>Todo:</h1>
  <ol>
    <!--
      Now we provide each todo-item with the todo object
      it's representing, so that its content can be dynamic.
      We also need to provide each component with a "key",
      which will be explained later.
    -->
    <li v-for="item in todos" v-bind:key="item.id">
      {{ item.text }}
    </li>
  </ol>
</div>
</template>

<script>
export default {
  name: "ToDoList",
  props: ['todos'],
  template:'<li>{{ item }}</li>'
}
</script>

<style scoped>

</style>