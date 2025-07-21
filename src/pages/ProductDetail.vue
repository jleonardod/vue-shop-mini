<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const product = ref(null)

onMounted(async () => {
  const productId = route.params.id
  const res = await fetch(`https://fakestoreapi.com/products/${productId}`)
  product.value = await res.json()
})
</script>

<template>
  <div class="w-full flex">
    <a href="#">Back</a>
    <p>Home - Product Detail</p>
  </div>
  <div>
    <h1>{{ product.title }}</h1>
    <p>{{ product.description }}</p>
    <p>{{ product.price }}</p>
  </div>
</template>