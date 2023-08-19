<template>
  <v-container class="container">
    <v-row>
      <v-col cols="12">
        <v-text-field v-model="newTask"></v-text-field>
        <v-btn  @click="addTask" color="green">Add Task</v-btn>
      </v-col>
    </v-row>
    <Tasks :tasks="tasks" @deleteTask="deleteTask" />
  </v-container>
</template>

<script>
import Tasks from "./Tasks.vue";

export default {
  name: "Container",
  components: {
    Tasks,
  },
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  created() {
    this.tasksFromLocal();
  },
  methods: {
    addTask() {
      if (!this.newTask) {
        return;
      }
      const counter = Date.now();
      this.tasks.push({ id: counter, text: this.newTask });
      window.localStorage.setItem(`task ${counter}`, this.newTask);
      this.newTask = "";
    },
    tasksFromLocal() {
      for (let i = 0; i < localStorage.length; i++) {
        const key = localStorage.key(i);
        if (key.startsWith("task")) {
          const taskId = key.replace("task", "").trim();
          const taskText = localStorage.getItem(key);
          this.tasks.push({ id: taskId, text: taskText });
        }
      }
    },
    deleteTask(taskId) {
      const updatedTasks = this.tasks.filter((task) => task.id !== taskId);
      this.tasks = updatedTasks;
      window.localStorage.removeItem(`task ${taskId}`);
    },
  },
};
</script>

