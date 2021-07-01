<template>
  <li>
    {{ item.id }}:{{ item.text }}
    <button @click="handleRemove(item.id)">Remove</button>
  </li>
</template>

<script>
export default {
  name: "ToDoItem",
  props: ['item'],
  emits: ['remove-item'],
  methods: {
    handleRemove(id){
      this.$emit('remove-item', id)
    }
  }
}
</script>

<style scoped>

</style>