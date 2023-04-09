<script setup>
import { defineProps, defineEmits } from "vue";

const emit = defineEmits(["selectOption"]);

const { question } = defineProps(["question"]);

const emitSelectedOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
</script>

<template>
  <div>
    <h2 class="lg:text-4xl text-3xl mx-2 lg:mx-0">{{ question.text }}</h2>

    <ul
      class="mt-10 mx-2 lg:mx-0 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg dark:bg-gray-700 dark:border-gray-600 dark:text-white"
    >
      <li
        v-for="option in question.options"
        @click="emitSelectedOption(option.isCorrect)"
        :key="option.id"
        class="w-full border-b border-gray-200 rounded-t-lg dark:border-gray-600"
      >
        <div class="flex items-center pl-3">
          <label
            for="vue-checkbox"
            class="w-full py-3 ml-2 text-2xl font-medium text-gray-900 dark:text-gray-300 cursor-pointer"
            >{{ option.text }}</label
          >
        </div>
      </li>
    </ul>
  </div>
</template>
