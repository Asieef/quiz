<script setup>
import { defineProps } from "vue";

const { quizes } = defineProps(["quizes"]);
</script>

<template>
  <div class="mt-12 mx-12 grid grid-cols-4 gap-4">
    <div
      v-for="quiz in quizes"
      :key="quiz.id"
      class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 col-span-1"
    >
      <a href="#">
        <img class="rounded-t-lg" :src="quiz.img" :alt="quiz.name" />
      </a>
      <div class="p-5">
        <a href="#">
          <h5
            class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
          >
            {{ quiz.name }}
          </h5>
        </a>
        <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">
          {{ quiz.questions.length }} Questions
        </p>
      </div>
    </div>
  </div>
</template>
