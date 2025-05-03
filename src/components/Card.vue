<template>
  <div :class="[cardData.cardColor, 'p-6 rounded-lg shadow-md']">
    <h2 class="text-2xl font-bold">{{ cardData.title }}</h2>
    <p class="mt-2 mb-4">{{ cardData.subtitle }}</p>
    <a
      href="jobs.html"
      :class="[
        cardData.buttonColor,
        `hover:${cardData.buttonHoverColor}`,
        'inline-block text-white rounded-lg px-4 py-2',
      ]"
    >
      {{ cardData.buttonText }}
    </a>
  </div>
</template>
<script setup lang="ts">
import { defineProps } from "vue";
const props = defineProps({
  cardType: {
    type: String,
  },
});
const cardData = {
  title: props.cardType === "dev" ? "For Developers" : "For Employers",
  subtitle:
    props.cardType === "dev"
      ? "Browse our Vue jobs and start your career today"
      : "List your job to find the perfect developer for the role",
  buttonText: props.cardType === "dev" ? "Browse Jobs" : "Add Jobs",
  cardColor: props.cardType === "dev" ? "bg-gray-100" : "bg-green-100 ",
  buttonColor: props.cardType === "dev" ? "bg-black" : "bg-green-500",
  buttonHoverColor: props.cardType === "dev" ? "bg-gray-700" : "bg-green-600",
};
</script>
