<template>
  <div>
    <p>Completed Tasks: {{ todos.filter(todo => todo.done).length }}</p>
    <p>Pending Tasks: {{ todos.filter(todo => !todo.done).length }}</p>
    <Todo
      v-for="(todo, index) in todos"
      :key="index"
      :todo="todo"
      v-on:delete-todo="deleteTodo"
      v-on:toggle-complete="toggleComplete"
    />
  </div>
</template>

<script>
import Todo from './Todo';
export default {
  components: {
    Todo
  },
  props: ['todos'],
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    toggleComplete(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = !this.todos[todoIndex].done;
    }
  }
};
</script>

<style scoped></style>
