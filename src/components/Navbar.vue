<script setup>
import { ShoppingBag, Github } from 'lucide-vue-next'
</script>
<template>
  <div class="bg-gray-800 px-8 py-4 text-white text-3xl font-bold flex items-center gap-2">
    <div class="flex items-center gap-2">
      <ShoppingBag class="inline-block mr-1 mt-1" />
      <h1>Lana</h1>
    </div>
    <div class="ml-auto">
      <a class="text-lg flex items-center font-semibold gap-x-2 hover:bg-white hover:text-black transition-colors cursor-pointer rounded border-1 py-1 px-3" href="https://github.com/jleonardod/vue-shop-mini" target="_blank">
        <Github />
        View Repo
      </a>
    </div>
  </div>
</template>