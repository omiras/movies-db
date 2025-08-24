<script setup>
import { ref } from "vue";
import { items } from "./movies.json";
/*
 This is an Icon that you can use to represent the stars if you like
 otherwise you could just use a simple ⭐️ emoji, or * character.
*/
import { StarIcon } from "@heroicons/vue/24/solid";

const cards = ref(items)

</script>

<template>
  <!-- This is where your template goes	-->

<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"
>
  <div v-for="card in cards" :key="card.id"
       class="bg-slate-50 text-gray-950 flex flex-col">

    <!-- Imagen con altura fija -->
    <img :src="card.image" :alt="card.name"
         class="h-64 w-full object-cover" />

    <div class="p-2 flex flex-col flex-grow">
      <div>
        <span
          v-for="g in card.genres"
          class="bg-violet-600 text-slate-100 rounded p-1 mr-1 inline-block"
        >
          {{ g }}
        </span>
        <h2 class="text-2xl">{{ card.name }}</h2>
        <p>{{ card.description }}</p>
      </div>

      <!-- Estrellas al final -->
      <div class="mt-auto">
        <div class="flex items-center gap-1">
          <span class="mr-2">Rating: {{ card.rating }}/5</span>
          <StarIcon
            v-for="r in card.rating"
            class="text-yellow-400 w-6"
          />
        </div>
      </div>
    </div>
  </div>
</div>

</template>

<style></style>
