<script setup>
import { ref } from "vue";
import { RouterView } from "vue-router";
import Nav from "./components/Nav.vue";
</script>

<template>
  <div>
    <Nav />
    <RouterView />
  </div>
</template>
