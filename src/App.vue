<template>
  <div id="app">
    <div class="container">
      <h1>Task Manager</h1>

      <div class="addAndFilterTasks">
        <div class="addTaskField">
          <AddTask @add-task-form="addTaskForm"></AddTask>
        </div>
        <div class="filterTask">
          <FilterTask
            :listItems="listItems"
            @select-val="filterTasks($event)"
          ></FilterTask>
        </div>
      </div>

      <div class="displayTask">
        <Tasks
          :tasks="this.tasks"
          @delete-task-list="deleteSelectedTask"
          @completeTaskCheck="completeTask"
        ></Tasks>
      </div>
    </div>
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
import FilterTask from "./components/FilterTask.vue";

export default {
  name: "App",
  components: {
    Tasks,
    AddTask,
    FilterTask,
  },
  emits: ["filterTasks"],
  data: function () {
    return {
      tasks: [
        { id: 1, name: "Lawn Mowing", completed: false },
        { id: 2, name: "Dog Walking", completed: false },
        { id: 3, name: "Workout", completed: true },
        { id: 4, name: "Grocery", completed: true },
      ],
      listItems: ["All", "Completed", "Incomplete"],
    };
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
    addTaskForm(addTask) {
      this.tasks.unshift(addTask);
    },
    filterTasks(a) {
      if (a === "All") {
        this.tasks = this.tasks.filter((task) => task);
      } else if (a === "Completed") {
        this.tasks = this.tasks.filter((task) => task.completed);
      } else if (a === "Incomplete") {
        this.tasks = this.tasks.filter((task) => !task.completed);
      }
      return this.tasks;
    },
  },
};
</script>

<style>
#app {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.addAndFilterTasks {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin-bottom: 40px;
}
.addTaskField {
  width: 70%;
}
</style>
