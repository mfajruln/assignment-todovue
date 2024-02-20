<template>
  <div class="todo-board">
    <h1>Todo List</h1>
    <TodoForm @addTodo="addTodo" />
    <TodoItems :todos="todos" @deleteTodo="deleteTodo" @editTodo="editTodo" />
  </div>
</template>

  
  <script>
  import TodoForm from './TodoForm.vue';
  import TodoItems from './TodoItems.vue';
  
  export default {
    name: 'TodoBoard',
    components: {
      TodoForm,
      TodoItems,
    },
    props: {
      todos: {
        type: Array,
        required: true,
      },
    },
    methods: {
      addTodo(todo) {
        this.$emit('addTodo', todo);
      },
      deleteTodo(index) {
        this.$emit('deleteTodo', index);
      },
      editTodo(payload) {
        this.$emit('editTodo', payload);
      },
    },
  };
  </script>

<style scoped>
.todo-board {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  background-color: #f5f5f5;
  border-radius: 8px;
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}
</style>