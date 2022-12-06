<template>
  <Header />
  
  <section class="bg-slate-100 grid grid-cols-3 gap-5">
    <Card v-for="product in products" :product="product"/>

  </section>
</template>

<script setup>
import Header from "./components/Header.vue";
import Card from "./components/Card.vue";
import { ref } from "vue";
const products = ref([]);
async function getProducts() {
  const data = await fetch("http://makeup-api.herokuapp.com/api/v1/products.json?brand=maybelline");
  const finalData = await data.json();
  products.value = finalData;
  console.log(products.value);
}
getProducts();

</script>

<style>
</style>
