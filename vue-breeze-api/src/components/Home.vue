<script setup>
// import { ref, onMounted } from "vue";
// import axios from "axios";

// const user = ref();
// onMounted(async () => {
//   await getToken();
//   const data = await axios.get("/api/user");
//   user.value = data.data;
//   //   console.log(user.value);
// });

// const getToken = async () => {
//   await axios.get("/sanctum/csrf-cookie");
// };

import { onMounted } from "vue";
import { useAuthStore } from "../stores/auth";

const authStore = useAuthStore();

onMounted(async () => {
  await authStore.getUser();
});
</script>
<template>
  <div v-if="authStore.user">
    <h1>{{ authStore.user.name }}</h1>
    <p>{{ authStore.user.email }}</p>
  </div>
  <div v-else>Go and Login</div>
</template>
