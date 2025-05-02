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
</template>

<script>
export default {
  setup() {
    const name = "John Doe";
    const status = "true";
    const tasks = ["Task 1", "Task 2", "Task 3", "Task 4"];

    const toggleActivity = () => {
      if (this.status === "true") {
        this.status = "false";
      } else {
        this.status = "true";
      }
    };
    return {
      name,
      status,
      tasks,
      toggleActivity,
    };
  },
};
</script>
