<template>
  <div>
    <TodoBoard :todos="todos" @addTodo="addTodo" @deleteTodo="deleteTodo" @editTodo="editTodo" @completedTodo="completedTodo" />
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
      // console.log(todo);
      this.todos.splice(index, 1, todo);
    },
    completedTodo(dataIndex){
      // console.log(dataIndex);
      if (this.todos[dataIndex].completed == true) {
        this.todos[dataIndex].completed = false;
      } else {
        this.todos[dataIndex].completed = true;
      }
      // console.log(this.todos);
    }
  },
};
</script>
