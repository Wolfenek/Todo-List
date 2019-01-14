<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todoItem="deleteTodoItem" />
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      // Implementing array of objects:
      todos: [
        {
          id: 1,
          title: 'Finish basic Vue tutorial',
          complete: false
        },
        {
          id: 2,
          title: 'Brush your teeth',
          complete: false
        },
        {
          id: 3,
          title: 'Add quantcast to page',
          complete: false
        }
      ]
    }
  },
  methods: {
    deleteTodoItem(id) {
      this.todos = this.todos.filter(todoItem => todoItem.id !== id);
    },
    addTodo(newTodo) {
        this.todos = [...this.todos, newTodo];
    }
  }
}
</script>

<style>
body {
  background-color: #2c3e50;
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #777;
}

::placeholder {
    color: #303030;
  }

</style>
