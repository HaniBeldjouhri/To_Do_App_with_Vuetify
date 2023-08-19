<template>
    <v-card class="task">
      <v-card-text style="font-size: 25px;">
        {{ task.text }}
      </v-card-text>
      <v-btn @click="deleteTask" class="Delete" color="red" >Delete</v-btn>
    </v-card>
  </template>
  
  <script>
  export default {
    name: "Task",
    props: {
      task: Object,
    },
    methods: {
      deleteTask() {
        this.$emit("deleteTask", this.task.id);
      },
    },
  };
  </script>
<style scoped>
.task{
    display: grid;
    
}
</style>  