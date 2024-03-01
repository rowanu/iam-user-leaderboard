<template>
  <h1 class="text-3xl font-bold text-gray-900">IAM User Leaderboard of Shame</h1>
  <ReadCSV @parsed-data="recieveData" />
  <div v-if="data">
    <UserBoard :data="data" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ReadCSV from './components/ReadCSV.vue';
import UserBoard from './components/UserBoard.vue';

const data = ref(null);

const recieveData = (recievedData) => {
  console.log('Recieved user data')
  data.value = recievedData
}

</script>