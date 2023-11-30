<template>
    <span class="go-back">
      <button @click="goBack">go back</button>
    </span>
  </template>
  
  <script setup lang="ts">
  import { useRouter } from 'vue-router';
  
  const goBack = () => {
    const router = useRouter();
    router.back();
  };
  </script>