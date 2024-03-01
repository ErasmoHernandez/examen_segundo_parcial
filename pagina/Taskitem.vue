<!-- TaskList.vue -->
<template>
    <div>
      <h2>Task List</h2>
      <ul>
        <task-item
          v-for="task in tasks"
          :key="task.id"
          :task="task"
          @toggle-completed="toggleCompleted"
          @delete-task="deleteTask"
        ></task-item>
      </ul>
      <input v-model="newTask" placeholder="Add a new task" />
      <button @click="addTask">Add Task</button>
    </div>
  </template>
  
  <script>
  import TaskItem from './Taskitem.vue';
  
  export default {
    components: {
      TaskItem,
    },
    data() {
      return {
        tasks: [
          { id: 1, title: 'Task 1', completed: false },
          { id: 2, title: 'Task 2', completed: true },
          // Add more tasks as needed
        ],
        newTask: '',
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() === '') return;
  
        const newTask = {
          id: this.tasks.length + 1,
          title: this.newTask,
          completed: false,
        };
  
        this.tasks.push(newTask);
        this.newTask = '';
      },
      toggleCompleted(taskId) {
        const task = this.tasks.find((task) => task.id === taskId);
        if (task) {
          task.completed = !task.completed;
        }
      },
      deleteTask(taskId) {
        this.tasks = this.tasks.filter((task) => task.id !== taskId);
      },
    },
  };
  </script>