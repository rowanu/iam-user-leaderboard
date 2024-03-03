<template>
  <table class="w-full text-center">
    <tr>
      <th>User</th>
      <th>ARN</th>
      <th>MFA enabled?</th>
    </tr>
    <tr v-for="item in enrichedData" :key="item.user">
      <td>{{ item.user }}</td>
      <td>{{ item.arn }}</td>
      <td>
        <span v-if="item.mfa_fail">
          <FontAwesomeIcon icon="fingerprint" class="text-red-500" /> FAIL
        </span>
        <span v-else>
          <FontAwesomeIcon icon="fingerprint" class="text-green-500" /> PASS
        </span>
      </td>
    </tr>
  </table>
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
</template>

<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { computed } from 'vue';

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
