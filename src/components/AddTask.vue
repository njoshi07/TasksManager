<template>
  <form @submit.prevent="submitForm">
    <div class="addTask">
      <div class="inputTask">
        <input
          v-model="name"
          class="form-control formInput"
          type="text"
          placeholder="Add Task Here And Press Enter"
        />
      </div>
      <!-- <div class="addTaskButton">
        <button type="submit" class="addButton btn btn-primary">
          Add Task
        </button>
      </div> -->
    </div>
  </form>
</template>

<script>
export default {
  data: function () {
    return { id: "", name: "", completed: false };
  },
  methods: {
    submitForm() {
      let addnewTask = {
        id: this.id,
        name: this.name,
        completed: this.completed,
      };
      document.querySelector(".formInput").value = "";
      return this.$emit("add-task-form", addnewTask);
    },
  },
};
</script>

<style>
/* .addTask {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin-bottom: 40px;
} */
/* .inputTask {
  width: 70%;
} */

/* .addTaskButton {
  margin: 0 0 0 20px;
} */
</style>