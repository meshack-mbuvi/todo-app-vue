<template>
  <div id="app">
    <TodoList :todos="todos" />
    <CreateTodo v-on:create-todo="addTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/createTodo';

export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo
  },
  data() {
    return {
      todos: [
        {
          title: 'Todo A',
          project: 'Project A',
          done: false
        },
        {
          title: 'Todo B',
          project: 'Project B',
          done: true
        },
        {
          title: 'Todo C',
          project: 'Project C',
          done: false
        },
        {
          title: 'Todo D',
          project: 'Project D',
          done: false
        }
      ]
    };
  },
  methods: {
    addTodo(todo) {
      console.log({ todo });
      this.todos = [...this.todos, todo];
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
