<template>
  <nav class="bg-slate-900 flex justify-around items-center py-5">
    <a href="#" class="text-white">AllProducts</a>
    <a href="#" class="text-white">Smartphones</a>
    <a href="#" class="text-white">Notebooks</a>

    <div class="container-button">
      
      <slot></slot>      
    </div> 
    </nav>
</template>

<script setup>
import {ref} from "vue";

</script>

<style>
.container-button {
  position:relative;
}
.purchase-counter {
  background-color: white;
  position: absolute;
  border-radius: 50%;
  width: 25px;
  height: 25px;
  text-align: center;
  top:-10%;
  right:-10%
}

</style>