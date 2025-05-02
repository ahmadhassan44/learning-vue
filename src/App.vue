<template>
  <p v-if="loading">Loading...</p>
  <div v-else>
    <h1>
      {{ name }}
    </h1>
    <p v-if="status === 'true'">{{ name }} is active</p>
    <p v-else-if="status === 'false'">{{ name }} is inactive</p>
    <p v-else>{{ name }}'s status is unknown</p>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">-</button>
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
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";

const name = "John Doe";
const status = ref("true");
const tasks = ref(["Task 1", "Task 2", "Task 3", "Task 4"]);
const newTask = ref("");
const loading = ref(false);

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
onMounted(async () => {
  try {
    loading.value = true;
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    tasks.value = await response.json().then((data) => {
      return data.map((task) => {
        return task.title;
      });
    });
    loading.value = false;
  } catch (error) {
    console.log("Error fetching data:", error);
    loading.value = false;
  }
});
const deleteTask = (index: number) => {
  tasks.value.splice(index, 1);
};
</script>
