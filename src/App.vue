<template>
  <Header>
    <img class="imageButton" src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTYuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjUxMnB4IiBoZWlnaHQ9IjUxMnB4IiB2aWV3Qm94PSIwIDAgNTEwIDUxMCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgNTEwIDUxMDsiIHhtbDpzcGFjZT0icHJlc2VydmUiPgo8Zz4KCTxnIGlkPSJzaG9wcGluZy1jYXJ0Ij4KCQk8cGF0aCBkPSJNMTUzLDQwOGMtMjguMDUsMC01MSwyMi45NS01MSw1MXMyMi45NSw1MSw1MSw1MXM1MS0yMi45NSw1MS01MVMxODEuMDUsNDA4LDE1Myw0MDh6IE0wLDB2NTFoNTFsOTEuOCwxOTMuOEwxMDcuMSwzMDYgICAgYy0yLjU1LDcuNjUtNS4xLDE3Ljg1LTUuMSwyNS41YzAsMjguMDUsMjIuOTUsNTEsNTEsNTFoMzA2di01MUgxNjMuMmMtMi41NSwwLTUuMS0yLjU1LTUuMS01LjF2LTIuNTUxbDIyLjk1LTQzLjM1aDE4OC43ICAgIGMyMC40LDAsMzUuNy0xMC4yLDQzLjM1LTI1LjVMNTA0LjksODkuMjVjNS4xLTUuMSw1LjEtNy42NSw1LjEtMTIuNzVjMC0xNS4zLTEwLjItMjUuNS0yNS41LTI1LjVIMTA3LjFMODQuMTUsMEgweiBNNDA4LDQwOCAgICBjLTI4LjA1LDAtNTEsMjIuOTUtNTEsNTFzMjIuOTUsNTEsNTEsNTFzNTEtMjIuOTUsNTEtNTFTNDM2LjA1LDQwOCw0MDgsNDA4eiIgZmlsbD0iI0ZGRkZGRiIvPgoJPC9nPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+Cjwvc3ZnPgo=">

  </Header>
  
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
.imageButton {
  width:20px;
  position:absolute;
  top:5%;
  right:10%
}
</style>
