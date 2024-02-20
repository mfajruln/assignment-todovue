<template>
    <table class="todo-list">
      <thead>
        <tr>
          <th>Task</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(todo, index) in todos" :key="index">
          <td>{{ todo.text }}</td>
          <td>
            <button @click="deleteTodo(index)" class="delete">Delete</button>
            <button @click="editMode(index)" class="edit">Edit</button>
            <input v-if="editing === index" type="text" v-model="editedTodo" @keyup.enter="editTodo(index)" @blur="cancelEdit" class="edit-input" />
          </td>
        </tr>
      </tbody>
    </table>
  </template>
  
  <script>
  export default {
    name: 'TodoItems',
    props: {
      todos: {
        type: Array,
        required: true,
      },
    },
    data() {
      return {
        editing: null,
        editedTodo: '',
      };
    },
    methods: {
      deleteTodo(index) {
        this.$emit('deleteTodo', index);
      },
      editMode(index) {
        this.editing = index;
        this.editedTodo = this.todos[index].text;
      },
      editTodo(index) {
        if (this.editedTodo.trim() !== '') {
          this.$emit('editTodo', { index: index, todo: { text: this.editedTodo, completed: false } });
          this.editing = null;
          this.editedTodo = '';
        }
      },
      cancelEdit() {
        this.editing = null;
        this.editedTodo = '';
      },
    },
  };
  </script>
  
  <style scoped>
  .todo-list {
    width: 100%;
    border-collapse: collapse;
  }
  
  th, td {
    padding: 10px;
    text-align: left;
    border-bottom: 1px solid #3498db; /* Blue (Primary) */
    color: #333; /* Text color */
  }
  
  th {
    background-color: #3498db; /* Blue (Primary) */
    color: white;
  }
  
  .delete {
    background-color: #e74c3c; /* Red */
    color: white;
    border: none;
    padding: 8px 12px;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .delete:hover {
    background-color: #c0392b; /* Darker Red */
  }
  
  .edit {
    background-color: #3498db; /* Blue (Primary) */
    color: white;
    border: none;
    padding: 8px 12px;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .edit:hover {
    background-color: #2980b9; /* Darker Blue */
  }
  </style>
  