<template>
    <div>
      <p>id: {{ props.id }}</p>
      <p>slug: {{ props.slug }}</p>
      <p>Destination: {{ destination}}</p>
    </div>
  </template>
  
  <script setup lang="ts">
  import dades from "@/data/data.json";
  import { defineProps, computed } from "vue";
  
  const props = defineProps({
    id: Number,
    slug: String,
  });
  
  const destination = computed(() =>
    dades.destinations.find((dest) => dest.id === props.id)
  );
  </script>
