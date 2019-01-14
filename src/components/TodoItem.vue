<template>
  <div class="todo-item" v-bind:class="{'is-complete':todoItem.complete}">
    <p>
      <input type="checkbox" v-on:change="markComplete">
      {{todoItem.title}}
      <button v-on:click="$emit('del-todoItem', todoItem.id)"
      class="del">
      x</button>
    </p>
  </div>
</template>

<script>
  export default {
   name: 'TodoItem',
   props: ['todoItem'],
   methods: {
     markComplete() {
       this.todoItem.complete = !this.todoItem.complete;
     }
   }
  }
</script>

<style scoped>
  .todo-item {
    background: blueviolet;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    text-align: center;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: yellow;
    color: #000;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }

</style>