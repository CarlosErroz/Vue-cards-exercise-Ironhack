<template>
  <article class="bg-white p-4 my-4 flex flex-col items-center">
    <img class="w-64" :src="product.image_link">
    <a href="#" class="my-4">{{product.name}}</a>
    <div class="flex flex-row justify-between my-3 min-w-full">
      <p>{{product.price}}€</p>
      <p>id: {{product.id}}</p>
    </div>
    <slot></slot>
    
  </article>
</template>

<script setup>
import {ref} from 'vue';
const props = defineProps(["product"]);

</script>

<style>

</style>