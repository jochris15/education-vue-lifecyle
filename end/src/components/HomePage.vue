<script setup>
// import data from "../assets/data.json";
import ProductCard from "./ProductCard.vue";
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";

const products = ref([]);

async function fetchProducts(url) {
  try {
    const response = await fetch(url);
    const data = await response.json();

    products.value = data.products;
  } catch (error) {
    console.error("Error fetching products:", error);
  }
}

fetchProducts("https://dummyjson.com/products");

onBeforeMount(() => {
  console.log("onBeforeMount");
});
onMounted(() => {
  console.log("onMounted");
});
onBeforeUpdate(() => {
  console.log("onBeforeUpdate");
});
onUpdated(() => {
  console.log("onUpdated");
});
onBeforeUnmount(() => {
  console.log("onBeforeUnmount");
});
onUnmounted(() => {
  console.log("onUnmounted");
});

// Option API example
// export default {
//   components : {
//     ProductCard
//   },
//   data() {
//     return {
//       products: data,
//     }
//   }
// }
</script>

<template>
  <!-- product list -->
  <div id="PAGE-HOME" class="min-h-screen flex items-center justify-center">
    <main class="my-5 bg-white grid grid-cols-4 gap-5">
      <div
        class="h-full flex flex-col justify-center items-center bg-yellow-400 border-2 border-black p-5 rounded-2xl shadow-[2px_2px_0px_rgba(0,0,0,1)]"
        v-for="product in products"
        :key="product.id"
      >
        <!-- // prop example -->
        <ProductCard :product="product" />
      </div>
    </main>
  </div>
</template>
