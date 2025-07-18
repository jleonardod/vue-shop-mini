<template>
  <div class="flex">
    <div class="w-[20%]">barra</div>
    <div class="w-full bg-black p-4 grid grid-cols-3 gap-10">
      <ProductCard 
        v-for="product in products" 
        :key="product.id" 
        :product="product"
      />
    </div>
  </div>
  
  
</template>

<script setup>
import { ref, onMounted } from 'vue'
import ProductCard from '../components/ProductCard.vue'

const products = ref([])

onMounted(async () => {
  const res = await fetch('https://fakestoreapi.com/products')
  products.value = await res.json()
  console.log(products.value)
})
</script>