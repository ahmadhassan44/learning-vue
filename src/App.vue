<template>
  <h1>
    {{ name }}
  </h1>
  <p v-if="status === 'true'">{{ name }} is active</p>
  <p v-else-if="status === 'false'">{{ name }} is inactive</p>
  <p v-else>{{ name }}'s status is unknown</p>
  <li v-for="task in tasks" :key="task">
    {{ task }}
  </li>
  <a :href="link" target="_blank">Google</a>
  <button @click="toggleActivity" style="display: block">
    Toggle Activity
  </button>
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <br />
    <input type="text" name="newTask" id="newTask" v-model="newTask" />
    <button type="submit">Add Task</button>
  </form>
</template>

<script setup>
import { ref } from "vue";

const name = "John Doe";
const status = ref("true");
const tasks = ref(["Task 1", "Task 2", "Task 3", "Task 4"]);
const newTask = ref("");

const toggleActivity = () => {
  if (status.value === "true") {
    status.value = "false";
  } else {
    status.value = "true";
  }
};
const addTask = () => {
  if (newTask.value !== "") tasks.value.push(newTask.value);
  newTask.value = "";
};
</script>
