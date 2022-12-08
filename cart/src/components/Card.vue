<template>
  <div class="grid grid-cols-3 gap-4 justify-items-center p-2 bg-gray-100">
    <div
      class="w-full max-w-sm bg-white rounded-lg shadow-md dark:bg-gray-800 dark:border-gray-700"
    >
      <a href="#">
        <img :src="item.img" class="p-8 rounded-t-lg" alt="product image" />
      </a>
      <div class="px-5 pb-5">
        <a
          href="#"
          class="text-xl font-semibold tracking-tight text-gray-900 dark:text-white"
        >
          <h5>{{ item.name }}</h5></a
        >

        <div class="flex items-center justify-between">
          <span
            class="text-gray-900 text-xs font-semibold mr-2 px-2.5 py-0.5 rounded dark:bg-blue-200 dark:text-blue-800 ml-3 mb-3"
            >R$ {{ item.price }}</span
          >

          <span
            class="text-gray-900 text-xs font-semibold mr-2 px-2.5 py-0.5 rounded dark:bg-blue-200 dark:text-blue-800 ml-3 mb-3"
            >10 x 226, 00</span
          >
        </div>
        <div class="flex flex-col items-center justify-between">
          <a
            href="#"
            class="text-white bg-green-500 hover:bg-green-900 focus:ring-4 focus:outline-none focus:bg-green-900 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-green-900 dark:hover:bg-green-900 dark:focus:bg-green-900"
            >Add to cart</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const item = ref({
  img: "",
  name: "",
  price: "",
});

async function getBeer() {
  const res = await fetch("https://api.punkapi.com/v2/beers");
  const finalRes = await res.json();

  item.value.img = finalRes[0].image_url;
  item.value.name = finalRes[0].name;
  item.value.price = finalRes[0].ibu;
}

getBeer();
</script>

<style></style>
