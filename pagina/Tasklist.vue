<!-- TaskItem.vue -->
<template>
    <li>
      <span :class="{ completed: task.completed }">{{ task.title }}</span>
      <button @click="toggleCompleted">Toggle Completed</button>
      <button @click="deleteTask">Delete</button>
    </li>
  </template>
  
  <script>
  export default {
    props: ['task'],
    methods: {
      toggleCompleted() {
        this.$emit('toggle-completed', this.task.id);
      },
      deleteTask() {
        this.$emit('delete-task', this.task.id);
      },
    },
  };
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }
  </style>