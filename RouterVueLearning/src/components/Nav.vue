<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <div>
    <RouterLink to="/" class="home" active-class="active">Home</RouterLink>
    <RouterLink to="/about" class="about" active-class="active"
      >About</RouterLink
    >
  </div>
</template>

<style scoped>
.home,
.about {
  margin: 0 8px;
  font-size: 32px;
  text-decoration: none;
  font-weight: bold;
}
.active {
  color: rgb(153, 104, 14);
}
</style>
