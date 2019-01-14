<template>
  <form @submit="addTodo">
    <input type="text" v-model="title" name="title" placeholder="Add todo...">
    <input type="submit" name="submit" value="Submit" class="btn">
  </form>
</template>

<script>
  export default {
    name: 'AddTodo',
    data() {
      return {
        title: ''
      }
    },
    methods: {
      addTodo(event) {
        event.preventDefault();
        const newTodo = {
          title: this.title,
          completed: false
        }
        // Send up to parent
        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    }
  }
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
    background: yellowgreen;
    color: #000;
    border: 1px #000 solid;
  }
</style>