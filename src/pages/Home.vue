<template>
  <ProductCard 
    v-for="product in products" 
    :key="product.id" 
    :product="product"
  />
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