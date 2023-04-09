<script setup>
import { defineProps } from "vue";

const { questionStatus, barPercentage } = defineProps([
  "questionStatus",
  "barPercentage",
]);
</script>

<template>
  <div>
    <header>
      <h4 class="lg:text-6xl text-3xl mb-3">Questions {{ questionStatus }}</h4>

      <div class="mb-6 b h-px w-full bg-neutral-200 dark:bg-neutral-600">
        <div class="h-px bg-blue-600" :style="{ width: barPercentage }"></div>
      </div>
      <div class="mb-6 h-5 w-full bg-neutral-200 dark:bg-neutral-600">
        <div class="h-5 bg-blue-500" :style="{ width: barPercentage }"></div>
      </div>
    </header>
  </div>
</template>
