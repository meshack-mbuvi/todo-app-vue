<template>
  <div class="ui centered card">
    <div class="content" v-show="!isEditing">
      <div class="header">{{ todo.title }}</div>
      <div class="meta">
        {{ todo.project }}
      </div>
      <div class="extra content">
        <span class="right floated edit icon" v-on:click="showForm">
          <i class="edit icon"></i>
        </span>

        <!-- trash icon here -->
        <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
          <i class="trash icon"></i>
        </span>
      </div>
    </div>
    <!-- form is visible when we are in editing mode -->
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <!-- title -->
        <div class="field">
          <label for="">Title</label>
          <input type="text" v-model="todo.title" />
        </div>
        <!-- Project -->
        <div class="field">
          <label for="">Project</label>
          <input type="text" v-model="todo.project" />
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div
      class="ui bottom attached green basic button"
      v-show="!isEditing && todo.done"
      v-on:click="toggleComplete(todo)"
      disabled
    >
      Completed
    </div>
    <div
      class="ui bottom attached red basic button"
      v-show="!isEditing && !todo.done"
      v-on:click="toggleComplete(todo)"
    >
      Pending
    </div>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  props: ['todo'],
  data() {
    return {
      isEditing: false
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    toggleComplete(todo) {
      this.$emit('toggle-complete', todo);
    }
  }
};
</script>
