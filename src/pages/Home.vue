<template>
  <h1>Hola mundo</h1>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const products = ref([])

onMounted(async () => {
  const res = await fetch('https://fakestoreapi.com/products')
  products.value = await res.json()
  console.log(products.value)
})
</script>