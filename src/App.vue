<template>
  <Navbar />
  <Hero title="Are you a vue dev?" subtitle="We have got you covered!" />
  <HomeCard />
  <JobListings limit="4" showButton="true" />
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import HomeCard from "./components/HomeCard.vue";
import JobListings from "./components/JobListings.vue";
</script>
