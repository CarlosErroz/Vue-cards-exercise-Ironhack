<template>
  <Header>
    <button class="text-white bg-cyan-500 rounded w-32 h-10 text-left pl-10" @click="showPurchase()">Cart</button>
    <img class="image-button" src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTYuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjUxMnB4IiBoZWlnaHQ9IjUxMnB4IiB2aWV3Qm94PSIwIDAgNTEwIDUxMCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgNTEwIDUxMDsiIHhtbDpzcGFjZT0icHJlc2VydmUiPgo8Zz4KCTxnIGlkPSJzaG9wcGluZy1jYXJ0Ij4KCQk8cGF0aCBkPSJNMTUzLDQwOGMtMjguMDUsMC01MSwyMi45NS01MSw1MXMyMi45NSw1MSw1MSw1MXM1MS0yMi45NSw1MS01MVMxODEuMDUsNDA4LDE1Myw0MDh6IE0wLDB2NTFoNTFsOTEuOCwxOTMuOEwxMDcuMSwzMDYgICAgYy0yLjU1LDcuNjUtNS4xLDE3Ljg1LTUuMSwyNS41YzAsMjguMDUsMjIuOTUsNTEsNTEsNTFoMzA2di01MUgxNjMuMmMtMi41NSwwLTUuMS0yLjU1LTUuMS01LjF2LTIuNTUxbDIyLjk1LTQzLjM1aDE4OC43ICAgIGMyMC40LDAsMzUuNy0xMC4yLDQzLjM1LTI1LjVMNTA0LjksODkuMjVjNS4xLTUuMSw1LjEtNy42NSw1LjEtMTIuNzVjMC0xNS4zLTEwLjItMjUuNS0yNS41LTI1LjVIMTA3LjFMODQuMTUsMEgweiBNNDA4LDQwOCAgICBjLTI4LjA1LDAtNTEsMjIuOTUtNTEsNTFzMjIuOTUsNTEsNTEsNTFzNTEtMjIuOTUsNTEtNTFTNDM2LjA1LDQwOCw0MDgsNDA4eiIgZmlsbD0iI0ZGRkZGRiIvPgoJPC9nPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+CjxnPgo8L2c+Cjwvc3ZnPgo=">
    <span class="purchase-counter" v-if="show">{{numberPurchase}}</span>
  </Header>
  
  <div class="background-purchase-list" @click="showPurchase()" v-if="showPurch">
  </div>

  <div class="purchase-list flex flex-col bg-slate-200" v-if="showPurch">
    <div class="w-10 h-10 bg-slate-200 detail"></div>
    <Subcard v-for="item in purchase" :item="item"></Subcard>
    <div>
      <p class="m-2 text-lg font-semibold">Total: {{ totalAmount }}€</p>
    </div>
  </div>

  <section class="bg-slate-100 grid grid-cols-3 gap-5">
    
    <Card v-for="product in products" :product="product">
      <button class="bg-green-500 rounded min-w-full h-10 text-white font-semibold" @click="buyProduct(product)">Add to cart</button>
    </Card>

  </section>
</template>

<script setup>
import Header from "./components/Header.vue";
import Card from "./components/Card.vue";
import Subcard from "./components/Subcard.vue";

import { ref } from "vue";
const products = ref([]);
async function getProducts() {
  const data = await fetch("http://makeup-api.herokuapp.com/api/v1/products.json?brand=maybelline");
  const finalData = await data.json();
  products.value = finalData;
}
getProducts();

const show = ref(false);
const numberPurchase = ref(0);
const purchase = ref([]);
const totalAmount = ref(0);

function buyProduct(product) {
  if (show.value == false) {
    show.value = true
  }
  numberPurchase.value += +1;
  purchase.value.push(product);
  totalAmount.value += Number(product.price);
  totalAmount.value.toFixed(2);
}

const showPurch = ref(false);

function showPurchase() {
  if (showPurch.value == false) {
    showPurch.value = true
  } else {showPurch.value = false}
  console.log(showPurch.value)
}

</script>

<style>
.image-button {
  width:20px;
  position:absolute;
  top:25%;
  right:25%
}
.background-purchase-list {
  position: absolute;
  width:100vw;
  height: 2000px;
  opacity:0.4;
  background-color: grey;
  top:0%;
}
.purchase-list {
  position: absolute;
  border-radius: 10px;
  z-index:1;
  width:500px;
  top:15%;
  right:20%;
  animation: appearUp;
  animation-duration: 0.5s;
}
.detail {
  position:absolute;
  z-index:-1;
  top:-5%;
  right:5%;
  transform:rotate(45deg);
}
@keyframes appearUp {
  from {
    margin-top:-100%;
  }

  to {
   margin-top:0%;
 }
}
</style>
