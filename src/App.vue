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
import axios from 'axios';

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
      todos: []
    }
  },
  methods: {
    deleteTodoItem(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todos.filter(todoItem => todoItem.id !== id))
        .catch(err => alert(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo; //destructuring

      axios.post('https://jsonplaceholder.typicode.com/todos?_limit', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => alert(err));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=3') // After "?" - sets the limit of items taken from API
      .then(res => this.todos = res.data)
      .catch(err => alert(err)); //change this later to something useful
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
