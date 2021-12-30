<template>
  <div>
    <div v-for="task in tasks" :key="task.id">
      <!-- <p>Hi there {{ task.completed }}</p> -->
      <Task
        :task="task"
        @delete-task="deleteTaskItem"
        @complete-task="completeTaskItem"
      ></Task>
    </div>
  </div>
</template>
<script>
import Task from "./Task.vue";
export default {
  name: "Tasks",
  components: {
    Task,
  },
  // data: function () {
  //   return {
  //     completed: this.task.completd,
  //   };
  // },

  props: {
    tasks: Array,
  },
  methods: {
    deleteTaskItem(tasks) {
      return this.$emit("delete-task-list", tasks);
    },
    completeTaskItem(id) {
      return this.$emit("completeTaskCheck", id);
    },
  },
};
</script>
<style>
</style>