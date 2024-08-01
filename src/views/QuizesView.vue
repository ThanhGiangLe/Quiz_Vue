<script setup>
import questions from "../data/quizes.json";
import { ref, watch } from "vue";
import Card from "../components/Card.vue";

const quizes = ref(questions); // Lưu danh sách quiz gốc
const search = ref(""); // Từ khóa tìm kiếm

// Dùng watch để mỗi lần có thay đổi giá trị truyền vào sẽ làm việc gì đó
watch(search, () => {
  quizes.value = questions.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <div>
    <header class="header-container">
      <h1>Quizes</h1>
      <input type="text" placeholder="Search..." v-model.trim="search" />
    </header>
    <div class="options-container">
      <!-- Sau khi import lấy Card bên trên lắp vào,  -->
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>
.header-container {
  margin: 10px 0;
  display: flex;
  align-items: center;
}
.header-container h1 {
  font-weight: bold;
  margin-right: 30px;
}
.header-container input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}
.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 32px;
}
</style>
