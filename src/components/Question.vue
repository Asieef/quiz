<script setup>
import { defineProps } from "vue";

const { question } = defineProps(["question"]);
</script>

<template>
  <div>
    <h2 class="text-4xl">{{ question.text }}</h2>

    <ul
      class="mt-10 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg dark:bg-gray-700 dark:border-gray-600 dark:text-white"
    >
      <li
        v-for="option in question.options"
        :key="option.id"
        class="w-full border-b border-gray-200 rounded-t-lg dark:border-gray-600"
      >
        <div class="flex items-center pl-3">
          <input
            id="vue-checkbox"
            type="radio"
            value=""
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
          />
          <label
            for="vue-checkbox"
            class="w-full py-3 ml-2 text-2xl font-medium text-gray-900 dark:text-gray-300"
            >{{ option.text }}</label
          >
        </div>
      </li>
    </ul>
  </div>
</template>
