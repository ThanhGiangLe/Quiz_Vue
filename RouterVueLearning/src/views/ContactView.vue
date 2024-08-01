<script setup>
import { useRoute } from "vue-router";
import cars from "../data/cars.json";
const route = useRoute();
const car = cars.find((car) => car.name === route.params.name);
</script>

<template>
  <div>
    <h1>Contact Info</h1>
    <table border="1">
      <tr>
        <th>Name: {{ car.contact.dealer }}</th>
      </tr>
      <tr>
        <th>Number: {{ car.contact.number }}</th>
      </tr>
    </table>
  </div>
</template>
