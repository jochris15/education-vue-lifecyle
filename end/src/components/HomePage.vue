<script setup>
// dengan menggunakan script setup kita tidak perlu mendeklarasikan export default & setup() secara manual

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
const loading = ref(false);

async function fetchProducts(url) {
  try {
    loading.value = true;
    const response = await fetch(url);
    const data = await response.json();

    products.value = data.products;
  } catch (error) {
    console.error("Error fetching products:", error);
  } finally {
    loading.value = false;
  }
}

fetchProducts("https://dummyjson.com/products");

onBeforeMount(() => {
  // biasanya digunakan untuk merubah data sebelum komponen di-mount, jarang digunakan
  console.log("lifecyle ini akan dipanggil sebelum komponen di-mount");
});

onMounted(() => {
  // biasanya digunakan untuk interaksi dengan DOM, contohnya untuk menginisialisasi plugin atau library yang membutuhkan DOM
  console.log("lifecyle ini akan dipanggil setelah komponen di-mount");
});

onBeforeUpdate(() => {
  // biasanya digunakan untuk merubah data sebelum komponen di-update, contohnya untuk menyimpan scroll position saat ini
  console.log("lifecyle ini akan dipanggil sebelum komponen di-update");
});

onUpdated(() => {
  // biasanya digunakan untuk interaksi dengan DOM yang sudah di-update, contohnya untuk restore scroll position setelah di update
  console.log("lifecyle ini akan dipanggil setelah komponen di-update");
});

onBeforeUnmount(() => {
  // biasanya digunakan untuk membersihkan event listener atau interval yang sudah di-set, contohnya untuk mematikan event lister untuk aplikasi realtime
  console.log("lifecyle ini akan dipanggil sebelum komponen di-unmount");
});

onUnmounted(() => {
  // biasanya digunakan untuk final cleanup, contohnya untuk disconnect dari external service
  console.log("lifecyle ini akan dipanggil setelah komponen di-unmount");
});

// Option API example
// export default {
//   components: {
//     ProductCard
//   },
//   data() {
//     return {
//       products: [],
//       loading: false,
//     }
//   },
//   methods: {
//     async fetchProducts(url) {
//       try {
//         this.loading = true;
//         const response = await fetch(url);
//         const data = await response.json();
//         this.products = data.products;
//       } catch (error) {
//         console.error("Error fetching products:", error);
//       } finally {
//         this.loading = false;
//       }
//     },
//   },
//   beforeCreate() {
//     console.log("lifecyle ini akan dipanggil sebelum instance dibuat");
//   },
//   created() {
//     console.log("lifecyle ini akan dipanggil setelah instance dibuat");
//     this.fetchProducts("https://dummyjson.com/products");
//   },
//   beforeMount() {
//     console.log("lifecyle ini akan dipanggil sebelum komponen di-mount");
//   },
//   mounted() {
//     console.log("lifecyle ini akan dipanggil setelah komponen di-mount");
//   },
//   beforeUpdate() {
//     console.log("lifecyle ini akan dipanggil sebelum komponen di-update");
//   },
//   updated() {
//     console.log("lifecyle ini akan dipanggil setelah komponen di-update");
//   },
//   beforeUnmount() {
//     console.log("lifecyle ini akan dipanggil sebelum komponen di-unmount");
//   },
//   unmounted() {
//     console.log("lifecyle ini akan dipanggil setelah komponen di-unmount");
//   }
// }
</script>

<template>
  <div class="flex flex-col items-center justify-center h-screen" v-if="loading">
    <img src="../assets/Bean Eater@1x-1.0s-200px-200px.svg" class="w-1/3" />
  </div>

  <!-- product list -->
  <div id="PAGE-HOME" class="min-h-screen flex items-center justify-center" v-else>
    <main class="my-5 bg-white grid grid-cols-4 gap-5">
      <div
        class="h-full flex flex-col justify-center items-center bg-yellow-400 border-2 border-black p-5 rounded-2xl shadow-[2px_2px_0px_rgba(0,0,0,1)]"
        v-for="product in products" :key="product.id">
        <!-- // prop example -->
        <ProductCard :product="product" />
      </div>
    </main>
  </div>
</template>
