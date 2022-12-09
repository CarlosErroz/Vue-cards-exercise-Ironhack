<template>
  <article class="bg-white m-2">
    <div class="flex flex-row items-center">
        <img class="w-24 mr-5 px-5" :src="item.image_link">
        <p class="font-semibold text-xl px-5">{{item.name}}</p>
    </div>
    <div>
      <p class="text-lg font-semibold w-100 text-right pr-10">{{item.price}}€</p>
    </div>
</article>

</template>

<script setup>
import {ref} from 'vue';
const props = defineProps(["item"]);
</script>

<style>

</style>