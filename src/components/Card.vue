<template>
  <article class="bg-white p-4 my-4 flex flex-col items-center">
    <img class="w-64 h-64" :src="product.image_link">
    <a href="#" class="my-4">{{product.name}}</a>
    <div class="flex flex-row justify-between my-3 min-w-full">
      <p>{{product.price}}€</p>
      <p>id: {{product.id}}</p>
    </div>
    <button class="bg-green-500 rounded min-w-full h-10 text-white font-semibold" @click="buyProduct(product)">Add to cart</button>
  </article>
</template>

<script setup>
import {ref} from 'vue';
const props = defineProps(["product"]);

const purchase = ref([]);

function buyProduct(product) {
  console.log(product);
}
</script>

<style>

</style>