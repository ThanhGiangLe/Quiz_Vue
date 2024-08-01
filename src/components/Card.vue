<script setup>
import { defineProps } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();
const props = defineProps({
  quiz: {
    type: Object,
    required: true,
  },
});
const navigateToQuiz = () => {
  router.push(`/quizes/${props.quiz.id}`);
};
</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quiz.img" alt="" />
    <div class="card-text">
      <h2>{{ props.quiz.name }}</h2>
      <p>{{ props.quiz.questions.length }} questions</p>
    </div>
  </div>
</template>

<style scoped>
/* Card */
.card {
  width: 310px;
  overflow: hidden;
  border-radius: 5px;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin: 0 20px 35px 0;
  cursor: pointer;
}
.card img {
  width: 100%;
  height: 190px;
  margin: 0;
  border-radius: 5px;
}
.card-text {
  padding: 0 5px;
}
.card-text h2 {
  font-weight: bold;
  margin: 6px 0;
}
.card-text p {
  margin: 0 0 4px 0;
}
</style>
