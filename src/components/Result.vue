<script setup>
import { defineProps } from "vue";
import { useRouter, RouterLink } from "vue-router";
const props = defineProps({
  quizQuestionLength: {
    type: Number,
    required: true,
  },
  numberOfCorrectAnswer: {
    type: Number,
    required: true,
  },
  currentQuestionIndex: {
    type: Number,
    required: true,
  },
});
const goBack = () => {};
</script>

<template>
  <div class="result">
    <p>Your Result...</p>
    <h1>{{ props.numberOfCorrectAnswer }}/{{ props.quizQuestionLength }}</h1>
    <span>Vào lại bài kiểm tra vào làm để xem kết quả!</span> <br />
    <RouterLink to="/" class="goBack">Go Back</RouterLink>
  </div>
</template>

<style scoped>
.result {
  text-align: center;
  padding: 100px 0;
}
p {
  font-size: 32px;
}
h1 {
  font-size: 80px;
}
span,
.goBack {
  font-size: 24px;
}
</style>
