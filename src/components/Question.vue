<script setup>
import { defineProps, defineEmits, ref, nextTick } from "vue";

const emit = defineEmits(["selectOption"]);
const props = defineProps({
  question: {
    type: Object,
    required: true,
  },
});
// Nhận sự kiện với biến "option" là lựa chọn được click
const clickOptionAnswer = (option) => {
  // Phát sự kiện với option đã chọn
  emit("selectOption", option);

  // Duyệt qua danh sách các đáp án của câu hỏi
  props.question.options.forEach((opt) => {
    // Nếu "opt" là câu trả lời đúng && khác với câu mình đã chọn
    if (opt.isCorrect === true && opt !== option) {
      opt.classTruee = 1;
    } else {
      // Ngược lại kiểm tra "option" đúng hay sai
      option.classTruee = option.isCorrect === true ? 1 : 0;
    }
  });
};
</script>

<template>
  <div class="question-container">
    <h1 class="question">{{ props.question.text }}?</h1>
  </div>
  <div class="options-container">
    <div
      class="option"
      v-for="option in props.question.options"
      :key="option.id"
      @click="clickOptionAnswer(option)"
    >
      <p class="option-lable">{{ option.label }}</p>
      <div
        :class="{
          'option-value': true,
          truee: option.classTruee == 1,
          falsee: option.classTruee == 0,
        }"
      >
        <p>{{ option.text }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 24px;
}
.quesstion {
  font-size: 40px;
  margin-bottom: 20px;
}
.option {
  display: flex;
  cursor: pointer;
  align-items: center;
  justify-content: center;
  margin-bottom: 12px;
}
.option-lable {
  background-color: bisque;
  width: 50px;
  height: 50px;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
}
.option-value {
  background-color: rgb(244, 239, 239);
  font-size: 30px;
  height: 100%;
  width: 100%;
  padding: 8px;
}
.option-value p {
  margin: 0;
}
.truee {
  background-color: rgb(17, 147, 17);
}
.falsee {
  background-color: rgb(204, 28, 31);
}
/* .bg-transition {
  animation: changeBackgroundColor 1s forwards;
}
@keyframes changeBackgroundColor {
  0% {
    background-color: white;
  }
  100% {
    background-color: rgb(17, 147, 17);
  }
} */
</style>
