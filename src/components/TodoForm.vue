<template>
    <form @submit.prevent="addTodo" class="todo-form">
      <input type="text" v-model="newTodo" placeholder="Add new todo" required class="todo-input" />
      <button type="submit" class="add-button">Add Todo</button>
    </form>
</template>
  
  <script>
  export default {
    name: 'TodoForm',
    data() {
      return {
        newTodo: '',
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== '') {
          this.$emit('addTodo', { text: this.newTodo, completed: false });
          this.newTodo = '';
        }
      },
    },
  };
  </script>
  
<style scoped>
.todo-form {
text-align: center;
}

.todo-input {
padding: 8px;
font-size: 16px;
border: 1px solid #3498db;
border-radius: 4px;
}

.add-button {
padding: 8px 16px;
font-size: 16px;
cursor: pointer;
border: none;
border-radius: 4px;
margin-left: 10px;
background-color: #2ecc71; /* Green (Success) */
color: white;
}

.add-button:hover {
background-color: #27ae60; /* Darker Green */
}
</style>