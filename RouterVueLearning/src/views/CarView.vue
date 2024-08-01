<script setup>
import { useRoute, useRouter, RouterLink } from "vue-router";
import cars from "../data/cars.json";
const route = useRoute();
const router = useRouter();
const carName = route.params.name;
const car = cars.find((car) => car.name === carName);
</script>

<template>
  <div>
    <h1>Car View</h1>
    <table border="1">
      <tr>
        <th>
          Name:
          {{ car.name }}
        </th>
      </tr>
      <tr>
        <th>
          Price:
          {{ car.price }}
        </th>
      </tr>
      <tr>
        <th>
          Year:
          {{ car.year }}
        </th>
      </tr>
    </table>
  </div>
  <button class="btn" @click="router.push(`/cars/${carName}/contact`)">
    Lick me for contact
  </button>
  <RouterView />
</template>
<style scoped>
.btn {
  margin-top: 32px;
}
</style>
