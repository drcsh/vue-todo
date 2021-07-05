<template>
  <li class="item">
    <span class="item-text">{{ item.text }}</span>
    <button class="done" @click="handleRemove(item.id)">Done!</button>
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
 .item {
   padding: 0.2em 0;
 }
 .item-text {
   font-family:'Roboto',sans-serif; 
 }
 .done {
   background-color: #42b983;
   display:inline-block;
   padding:0.3em 1.2em;
   margin-left: 1em;
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
 .done:hover {
   background-color:#4eb5f1;
 }
</style>