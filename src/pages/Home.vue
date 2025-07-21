<template>
  <div class="flex">
    <div class="w-full bg-[#F4F4F5] text-white p-4 flex flex-col gap-y-4">
      <div>
        <h2 class="font-bold text-3xl text-[#111827]">Nuestros Productos</h2>
        <p class="text-sm text-[#111827]">Prueba cualquiera de nuestros productos, te aseguramos que no te arrepentirás</p>
      </div>
      <div class="grid grid-cols-4 gap-y-5 gap-x-4">
        <ProductCard 
          v-for="product in products" 
          :key="product.id" 
          :product="product"
        />
      </div>
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

<style>
.product-card:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  transition: all 0.2s ease;
}
.product-card{
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}
</style>