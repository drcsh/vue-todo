<template>
  <div>
    <label>
      To Do:
      <input v-bind:name="inputName" type="text" v-model="input" placeholder="Great things..."/>
    </label>
  </div>
</template>
<script>
export default {
  name: 'NewToDoInput',
  props:['inputName']
}
</script>

<style scoped>

</style>