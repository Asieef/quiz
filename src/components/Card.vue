<script setup>
import { defineProps } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

const { quiz } = defineProps(["quiz"]);

const navigateToQuiz = () => {
  router.push(`/quiz/${quiz.id}`);
};
</script>

<template>
  <div @click="navigateToQuiz" class="mt-12">
    <div
      class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
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
