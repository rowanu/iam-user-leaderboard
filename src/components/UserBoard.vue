<template>
  <div class="w-full p-4 m-4">
    <ol class="list-decimal">
      <li v-for="item in enrichedData" :key="item.user" class="p-1">
        {{ item.user }}
        <span v-if="item.mfa_fail">
          <font-awesome-icon icon="fingerprint" class="text-red-500" /> FAIL
        </span>
        <span v-else>
          <font-awesome-icon icon="fingerprint" class="text-green-500" /> PASS
        </span>
      </li>
    </ol>
  </div>
  <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
    @click="showRawData = !showRawData">Show Raw Data</button>
  <div :class="{ hidden: !showRawData }">
    <h3 class="text-xl">Raw data</h3>
    <table class="w-full">
      <tr>
        <th>User</th>
        <th>ARN</th>
        <th>User Creation Time</th>
        <th>Password Enabled</th>
        <th>Password Last Used</th>
        <th>Password Last Changed</th>
        <th>Password Next Rotation</th>
        <th>MFA Active</th>
        <th>Access Key 1 Active</th>
        <th>Access Key 1 Last Rotated</th>
        <th>Access Key 1 Last Used Date</th>
        <th>Access Key 1 Last Used Region</th>
        <th>Access Key 1 Last Used Service</th>
        <th>Access Key 2 Active</th>
        <th>Access Key 2 Last Rotated</th>
        <th>Access Key 2 Last Used Date</th>
        <th>Access Key 2 Last Used Region</th>
        <th>Access Key 2 Last Used Service</th>
        <th>Cert 1 Active</th>
        <th>Cert 1 Last Rotated</th>
        <th>Cert 2 Active</th>
        <th>Cert 2 Last Rotated</th>
      </tr>
      <tr v-for="item in enrichedData" :key="item.user">
        <td>{{ item.user }}</td>
        <td>{{ item.arn }}</td>
        <td>{{ item.user_creation_time }}</td>
        <td>{{ item.password_enabled }}</td>
        <td>{{ item.password_last_used }}</td>
        <td>{{ item.password_last_changed }}</td>
        <td>{{ item.password_next_rotation }}</td>
        <td>{{ item.mfa_active }}</td>
        <td>{{ item.access_key_1_active }}</td>
        <td>{{ item.access_key_1_last_rotated }}</td>
        <td>{{ item.access_key_1_last_used_date }}</td>
        <td>{{ item.access_key_1_last_used_region }}</td>
        <td>{{ item.access_key_1_last_used_service }}</td>
        <td>{{ item.access_key_2_active }}</td>
        <td>{{ item.access_key_2_last_rotated }}</td>
        <td>{{ item.access_key_2_last_used_date }}</td>
        <td>{{ item.access_key_2_last_used_region }}</td>
        <td>{{ item.access_key_2_last_used_service }}</td>
        <td>{{ item.cert_1_active }}</td>
        <td>{{ item.cert_1_last_rotated }}</td>
        <td>{{ item.cert_2_active }}</td>
        <td>{{ item.cert_2_last_rotated }}</td>
      </tr>
    </table>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

let showRawData = ref(false)

const props = defineProps({
  data: {
    type: Array,
    required: true,
  },
})

const enrichedData = computed(() => {
  return props.data.map((item) => {
    return {
      ...item,
      mfa_fail: !item.mfa_active,
      // user_creation_time: new Date(item.user_creation_time).toLocaleString(),
      // password_last_used: new Date(item.password_last_used).toLocaleString(),
      // password_last_changed: new Date(item.password_last_changed).toLocaleString(),
      // password_next_rotation: new Date(item.password_next_rotation).toLocaleString(),
      // access_key_1_last_used_date: new Date(item.access_key_1_last_used).toLocaleString(),
      // access_key_1_last_used_region: new Date(item.access_key_1_last_used_region).toLocaleString(),
      // access_key_1_last_used_service: new Date(item.access_key_1_last_used_service).toLocaleString(),
      // access_key_2_last_used_date: new Date(item.access_key_2_last_used).toLocaleString(),
      // access_key_2_last_used_region: new Date(item.access_key_2_last_used_region).toLocaleString(),
      // access_key_2_last_used_service: new Date(item.access_key_2_last_used_service).toLocaleString(),
      // cert_1_last_rotated: new Date(item.cert_1_last_rotated).toLocaleString(),
      // cert_2_last_rotated: new Date(item.cert_2_last_rotated).toLocaleString(),
    }
  })
})
</script>
