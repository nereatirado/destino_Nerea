<template>
  <div>
    <GoBack />
    <h1>{{ destination?.name }}</h1>

    <div class="informacion">
      <div class="img">
        <img :src="`../img/${destination?.image}`" alt="">
      </div>
      <div class="informacionDestino">
        <p>{{ destination?.description }}</p>
      </div>
    </div>

    <h1>Top experiences in {{ destination?.name }}</h1>
    <section class="experiencias" v-if="destination">
      <RouterLink
        v-for="experience in destination.experiences"
        :key="experience.slug"
        :to="{ name: 'experience.show', params: { slug: experience.slug } }"
      >
        <div class="experiencia">
          <img :src="`../img/${experience.image}`" width="60" class="img2" alt="">
          <p class="nombre">{{ experience.name }}</p>
        </div>
      </RouterLink>
    </section>
    <RouterView></RouterView>
  </div>
</template>

<script setup lang="ts">
import { defineProps, computed } from "vue";
import { RouterLink, RouterView } from "vue-router";
import dades from "@/data/data.json";
import GoBack from "@/components/GoBack.vue";

const props = defineProps(["id"]);

const destination = computed(() =>
  dades.destinations.find((dest) => dest.id === props.id)
);
</script>
  
  <style scoped>
  img {
    width: 600px;
  }
  
  h1 {
    padding: 50px;
    padding-left: 5%;
    text-align: center;
    color: #2c3e50;
  }
  
  .informacion,
  .experiencias {
    display: flex;
    margin: 0 auto;
    width: 90%;
    margin-bottom: 15px;
  }
  
  .img {
    width: 40%;
  }
  
  .informacionDestino {
    width: 60%;
    margin-left: 200px;
  }
  
  .destination-info p {
    padding: 50px;
    text-align: justify;
  }
  
  .experiencia {
    width: 75%;
  }
  
  .img2 {
    max-width: 100%;
    height: 200px;
    display: block;
  }
  
  .nombre {
    background-color: #2c3e50;
    color: white;
    text-decoration: none;
  }
  </style>
  