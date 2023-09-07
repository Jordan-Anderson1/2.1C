<template>
  <div class="todo-app">
  <h1>Todo App</h1>
  <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
  <ul>
  <li v-for="(task, index) in tasks" :key="index">
  <input type="checkbox" v-model="task.completed">
  <span :class="{ completed: task.completed }">{{ task.text }}</span>
  <button @click="removeTask(index)">Remove</button>
  </li>
  </ul>
  </div>
 </template>
  
 <script>
 export default {
  data() {
  return {
  newTask: '',
  tasks: []
  };
  },
  methods: {
  addTask() {
  if (this.newTask.trim() !== '') {
  this.tasks.push({
  text: this.newTask,
  completed: false
  });
  this.newTask = '';
  }
  },
  removeTask(index) {
  this.tasks.splice(index, 1);
  }
  }
 };
 </script>
  
  
  <style scoped>
  /* Style the outer container */
  .todo-app {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f9f9f9;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    transition: background-color 0.3s ease;
  }

  /* Style the heading */
  h1 {
    font-size: 24px;
    text-align: center;
    margin-bottom: 20px;
    color: #333;
  }

  /* Style the input for adding tasks */
  input[type="text"] {
    width: 100%;
    padding: 12px;
    font-size: 16px;
    border: none;
    border-radius: 5px;
    margin-bottom: 10px;
    background-color: #fff;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  /* Style the task list */
  ul {
    list-style-type: none;
    padding: 0;
  }

  /* Style individual task items */
  li {
    display: flex;
    align-items: center;
    padding: 10px;
    background-color: #fff;
    border-radius: 5px;
    margin-bottom: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s ease;
  }

  /* Style the checkbox */
  input[type="checkbox"] {
    margin-right: 10px;
  }

  /* Style completed tasks */
  .completed {
    text-decoration: line-through;
    color: #888;
  }

  /* Style the remove button */
  button {
    background-color: #e74c3c;
    color: #fff;
    border: none;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  /* Hover effect for the remove button */
  button:hover {
    background-color: #c0392b;
  }
</style>
