<script setup>
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import Result from "../components/Result.vue";
import { useRoute } from "vue-router";
import { ref, watch, computed } from "vue";
import quizes from "../data/quizes.json";

const route = useRoute();

const quizId = parseInt(route.params.id);
const CurrentQuestionIndex = ref(0);
const quiz = quizes.find((q) => q.id === quizId);
const numberofCorrectAnswers = ref(0);
const showResult = ref(false);

const questionStatus = computed(() => {
  return `${CurrentQuestionIndex.value}/${quiz.questions.length}`;
});

const barPercentage = computed(
  () => `${(CurrentQuestionIndex.value / quiz.questions.length) * 100}%`
);

const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberofCorrectAnswers.value++;
  }
  if (quiz.questions.length - 1 === CurrentQuestionIndex.value) {
    showResult.value = true;
  }

  CurrentQuestionIndex.value++;
};
</script>

<template>
  <div>
    <div>
      <QuizHeader
        :questionStatus="questionStatus"
        :barPercentage="barPercentage"
      />
    </div>
    <div>
      <Question
        v-if="!showResult"
        :question="quiz.questions[CurrentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
      <Result
        v-else
        :quizQuestionLength="quiz.questions.length"
        :numberofCorrectAnswers="numberofCorrectAnswers"
      />
    </div>
  </div>
</template>
