<template>
  <div class="filterTask">
    <label for="tasks">Filter Tasks:</label>
    <select
      v-model="selectedOption"
      name="tasks"
      id="tasks"
      @change="selectVal"
    >
      <option disabled value="">Select one</option>
      <option
        :value="listItem"
        v-for="(listItem, index) in listItems"
        :key="index"
      >
        {{ listItem }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      selectedOption: "",
    };
  },
  props: ["listItems"],

  methods: {
    selectVal() {
      return this.$emit("select-val", this.selectedOption);
    },
  },
};
</script>

<style scoped>
.filterTask {
  margin: 0 10px;
}
</style>