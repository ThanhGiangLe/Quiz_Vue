<script setup>
import { defineProps } from "vue";

const props = defineProps({
  questionStatus: {
    type: String,
    required: true,
  },
  barPercentage: {
    type: Number,
    required: true,
  },
});
</script>

<template>
  <header>
    <h3>Questions {{ props.questionStatus }}</h3>
    <div class="bar">
      <div class="completion" :style="{ width: props.barPercentage }"></div>
    </div>
  </header>
</template>
<style scoped>
header {
  margin-top: 24px;
}
header h3 {
  font-size: 32px;
  margin: 4px 0;
}
.bar {
  width: 300px;
  height: 50px;
  border: 2px solid #333;
}
.completion {
  height: 100%;
  width: 0%;
  max-width: 100%;
  overflow: hidden;
  background-color: bisque;
}
</style>
