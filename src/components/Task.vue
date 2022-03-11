<template>
  <div
    class="
      highlight
      d-flex
      justify-content-between
      align-items-center
      bd-highlight
      mb-3
    "
  >
    <div class="d-flex align-items-center m-3">
      <div class="me-3">
        <input type="checkbox" id="" name="" @click="completeTask(task.id)" />
      </div>
      <div>
        <label
          class="fs-3 align-middle"
          :class="task.completed === true ? 'is-completed' : ''"
          for=""
          >{{ task.name }}</label
        >
      </div>
    </div>

    <div class="m-3">
      <button @click="deleteTask(task)" class="btn">x</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["task"],
  data: function () {
    return {
      completed: this.task.completed,
    };
  },
  methods: {
    deleteTask(task) {
      return this.$emit("delete-task", task);
    },
    completeTask(id) {
      this.$emit("complete-task", id);
    },
  },
};
</script>

<style scoped>
.highlight {
  background-color: #eee;
}
.is-completed {
  text-decoration: line-through;
}
</style>