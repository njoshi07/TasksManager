<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <div class="container">
      <h1>Task Manager</h1>
      <div>
        <Tasks
          :tasks="tasks"
          @delete-task-list="deleteSelectedTask"
          @completeTaskCheck="completeTask"
        ></Tasks>
      </div>
    </div>
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";

export default {
  name: "App",
  components: {
    Tasks,
  },
  data: function () {
    return {
      tasks: [],
    };
  },
  created() {
    this.tasks = [
      { id: 1, name: "Lawn Mowing", completed: false },
      { id: 2, name: "Dog Walking", completed: false },
      { id: 3, name: "Workout", completed: true },
      { id: 4, name: "Grocery", completed: true },
      { id: 5, name: "Yard Cleaning", completed: true },
      { id: 6, name: "fix Lights", completed: false },
      { id: 7, name: "test", completed: false },
    ];
  },
  methods: {
    deleteSelectedTask(tasks) {
      const result = this.tasks.filter((task) => task.id !== tasks.id);
      this.tasks = result;
    },
    completeTask(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, completed: !task.completed } : task
      );
    },
  },
};
</script>

<style>
</style>
