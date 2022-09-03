<template>
  <div :class="`task ${task.done ? 'is-complete' : ''}`">
    <div class="content">
      {{ task.content }}
    </div>
    <div class="buttons">
      <button @click="toggleDone">{{ task.done ? "Undo" : "Done" }}</button>
      <button @click="deleteTask" class="delete">Delete</button>
    </div>
  </div>
</template>
<script>
export default {
  props: ["task"],
  methods: {
    toggleDone() {
      this.$store.commit("TOGGLE_TASK", this.task);
    },
    deleteTask(task) {
      this.$store.commit("REMOVE_TASK", this.task);
    },
  },
};
</script>