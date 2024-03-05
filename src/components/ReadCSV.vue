<template>
  <div class="space-y-4">
    <div>
      Load an <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_getting-report.html"
        target="_blank">IAM credential report</a>.
      Your credential report file does not contain any credentials, and is not shared externally.
      All processing happens locally in your browser.
    </div>
    <div class="mt-1 flex px-6 pt-5 pb-6 border-2 border-gray-300 border-dashed rounded-md">
      <div class="space-y-1 text-center">
        <div class="flex text-sm text-gray-600">
          <button type="button"
            class="group relative w-full py-2 px-4 border border-gray-300 rounded-md shadow-sm text-left text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
            @click="$refs.fileInput.click()">
            <input type="file" ref="fileInput" class="hidden" accept=".csv" @change="uploadFile($event)">
            <img src="../assets/csv.svg" alt="A CSV file"
              class="w-6 h-6 inline-block mr-2 group-hover:text-indigo-600" />
            <span>Load a file</span>
          </button>
        </div>
      </div>
    </div>
    <div>
      <h3 class="text-xl">Key</h3>
      <div>
        <FontAwesomeIcon icon="fingerprint" /> MFA shoould enabled if the user uses a password, or is a root user.
        <FontAwesomeIcon icon="key" /> Access keys should only be used by users with no password.
      </div>
    </div>
  </div>
</template>

<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { parse } from 'papaparse'

const emit = defineEmits(['parsed-data'])

function uploadFile(event) {
  const file = event.target.files[0]
  const reader = new FileReader()
  reader.onload = (event) => {
    const results = parse(event.target.result, {
      header: true,
      dynamicTyping: true,
      skipEmptyLines: true,
    })
    emit('parsed-data', results.data)
  }
  reader.readAsText(file)
}

</script>

<style scoped></style>
