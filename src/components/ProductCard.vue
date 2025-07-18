<script setup>
defineProps({
  product: Object
})
</script>

<template>
  <router-link to="/" class="flex flex-col h-[400px] items-center border-2 border-gray-700 bg-gray-700 hover:bg-purple-900 hover:border-purple-900 transition-colors rounded-lg ">
    <div class="w-full bg-white rounded-t-lg h-[70%] row-span-3 py-4 px-2">
      <img :src="product.image" alt="" class="object-contain w-full h-full" />
    </div>
    <div class="w-full h-[30%] row-span-2 border-t-2 rounded-b-sm text-white flex flex-col items-center justify-center gap-2 leading-4 px-3">
      <h2 class="font-semibold text-center">{{ product.title }}</h2>
      <p class="font-semibold text-xl">$ {{ product.price }}</p>
    </div>
  </router-link>
</template>