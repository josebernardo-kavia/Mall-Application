<script setup>
import { ref, onMounted } from "vue";

const message = ref("Loading...");

onMounted(async () => {
  try {
    const response = await fetch("http://localhost:8001/hello");
    message.value = await response.text();
  } catch (error) {
    console.error("Error:", error);
    message.value = "Error connecting to backend";
  }
});

</script>

<template>
  <h1>{{ message }}</h1>
</template>
