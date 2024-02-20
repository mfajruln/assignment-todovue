<template>
  <div>
    <TodoBoard :todos="todos" @addTodo="addTodo" @deleteTodo="deleteTodo" @editTodo="editTodo" />
  </div>
</template>

<script>
import TodoBoard from './components/TodoBoard.vue';

export default {
  name: 'App',
  components: {
    TodoBoard,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    editTodo({ index, todo }) {
      this.todos.splice(index, 1, todo);
    },
  },
};
</script>
