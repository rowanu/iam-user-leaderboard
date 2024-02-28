<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1 class="text-4xl font-bold">{{ msg }}</h1>

  <div class="bg-white border p-6 rounded shadow">
    <button type="button" class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded"
      @click="count++">count is {{ count }}</button>
    <p class="text-gray-500">
      Edit
      <code class="text-sm font-mono bg-gray-100 px-1">components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p class="text-sm text-gray-500">
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      class="font-bold hover:underline">create-vue</a>
    , the official Vue + Vite starter
  </p>
  <p class="text-sm text-gray-500">
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank" class="font-bold hover:underline">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="text-xs text-gray-500">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped></style>
