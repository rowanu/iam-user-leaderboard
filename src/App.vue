<script setup>
import ReadCSV from './components/ReadCSV.vue';
</script>

<template>
  <h1 class="text-3xl font-bold text-gray-900">IAM User Leaderboard of Shame</h1>
  <ReadCSV />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
