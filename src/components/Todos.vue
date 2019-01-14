<template>
  <div>
    <div v-bind:key="todoItem.id" v-for="todoItem in todos">
      <TodoItem v-bind:todoItem="todoItem" v-on:del-todoItem="$emit('del-todoItem', todoItem.id)" />  
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

  export default {
    name: 'Todos',
    components: {
      TodoItem
    },
    props: ['todos']
  }
</script>

<style scoped>
  
</style>