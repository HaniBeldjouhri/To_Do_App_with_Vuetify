<template>
    <v-container class="tasks">
      <Task
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @deleteTask="deleteTask"
      />
    </v-container>
  </template>
  
  <script>
  import Task from "./Task.vue";
  
  export default {
    name: "Tasks",
    components: {
      Task,
    },
    props: {
      tasks: Array,
    },
    methods: {
      deleteTask(taskId) {
        let updatedTasks = this.tasks.filter((task) => task.id !== taskId);
        this.$emit("deleteTask", taskId, updatedTasks);
      },
    },
  };
  </script>
<style scoped>
.tasks{
    display: grid;
    gap:20px;
}
</style>    