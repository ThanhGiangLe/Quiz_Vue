<script setup>
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import Result from "../components/Result.vue";
import { useRoute } from "vue-router";
import { ref, computed } from "vue";
import quizes from "../data/quizes.json";

const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizes.find((q) => q.id === quizId);
const currentQuestionIndex = ref(0);
const numberOfCorrectAnswer = ref(0);
const showResults = ref(false); // Biến dùng để kiểm tra có show file Result lên hay không. Mặc định là không
// Dùng để tính số lượng câu hỏi trên tổng số
const questionStatus = computed(
  () => `${currentQuestionIndex.value}/${quiz.questions.length}`
);
// Dùng để tính thanh hiển thị phần trăm cho tổng số câu trả lời
const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);
const onOptionSelected = (option) => {
  if (option.isCorrect === true) {
    numberOfCorrectAnswer.value++;
  }
  if (currentQuestionIndex.value === quiz.questions.length - 1) {
    showResults.value = true;
  }
  currentQuestionIndex.value++;
};
</script>

<template>
  <div>
    <QuizHeader
      :questionStatus="questionStatus"
      :barPercentage="barPercentage"
    />
    <div>
      <Question
        v-if="!showResults"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
      <Result
        v-else
        :quizQuestionLength="quiz.questions.length"
        :numberOfCorrectAnswer="numberOfCorrectAnswer"
      />
    </div>
    <button v-if="!showResults" @click="onOptionSelected">Next Question</button>
  </div>
</template>

<style scoped>
button {
  padding: 10px;
}
</style>
