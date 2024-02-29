<template>
  <div class="space-y-4">
    <h1 class="text-3xl font-bold text-gray-900">Read a Credential Report file</h1>
    <div>
      Your file is not shared externally - It is only read locally in your browser.
    </div>
    <div class="mt-1 flex justify-center px-6 pt-5 pb-6 border-2 border-gray-300 border-dashed rounded-md">
      <div class="space-y-1 text-center">
        <svg class="mx-auto h-12 w-12 text-gray-400" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
          stroke="currentColor" aria-hidden="true">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
            d="M3 7v10a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-6l-2-2H5a2 2 0 00-2 2z" />
        </svg>
        <div class="flex text-sm text-gray-600">
          <label for="file-input"
            class="relative cursor-pointer bg-white rounded-md font-medium text-indigo-600 hover:text-indigo-500 focus-within:outline-none focus-within:ring-2 focus-within:ring-offset-2 focus-within:ring-indigo-500">
            <span>Upload a file</span>
            <input id="file-input" name="file" type="file" class="sr-only" @change="uploadFile" />
          </label>
        </div>
      </div>
    </div>
    <div v-if="csvText">
      <h2 class="text-lg leading-6 font-medium text-gray-900">Parsed CSV</h2>
      <pre class="mt-3 bg-white rounded-md text-sm p-4">{{ csvText }}</pre>
      <div>{{ csvData }}</div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { parse } from 'papaparse'

const csvText = ref(null)
const csvData = ref(null)

function uploadFile(event) {
  const file = event.target.files[0]
  const reader = new FileReader()
  reader.onload = (event) => {
    const results = parse(event.target.result, {
      header: true,
      dynamicTyping: true,
      skipEmptyLines: true,
    })
    csvData.value = results.data
    csvText.value = event.target.result
  }
  reader.readAsText(file)
}

</script>

<style scoped></style>
