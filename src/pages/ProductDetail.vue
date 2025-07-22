<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import { ArrowLeft, CalendarDays, CirclePercent, Package, Store } from 'lucide-vue-next'

const route = useRoute()
const product = ref(null)

onMounted(async () => {
  const productId = route.params.id
  const res = await fetch(`https://fakestoreapi.com/products/${productId}`)
  product.value = await res.json()
})
</script>
<script>
export default {
  methods: {
    mostrarAlerta() {
      alert('Feature not implemented yet!')
    }
  }
}
</script>

<template>
  <div class="p-4 min-h-screen bg-[#F4F4F5] gap-y-4 flex flex-col">
    <div class="w-2/5 flex gap-x-2 text-gray-700">
      <button @click="$router.back()" class="cursor-pointer transition-colors hover:text-black"><ArrowLeft /></button>
      <div class="flex items-center gap-x-2 font-semibold transition-all">
        <a class="cursor-pointer text-md hover:underline hover:text-black ">Home</a>
        <span class="text-gray-500">-</span>
        <p class="cursor-pointer">Product Detail</p>
      </div>
    </div>
    <div v-if="product" class="grid grid-cols-2 gap-x-6 w-full">
      <div class="bg-white shadow-xl rounded-lg p-8 items-center flex flex-col">
        <img :src="product.image" alt="" class="object-cover h-[450px]" />
      </div>
      <div class="p-4 flex flex-col gap-y-4">
        <div class="flex flex-col gap-y-2">
          <h2 class="text-4xl font-bold">{{ product.title }}</h2>
          <p class="text-gray-700 text-3xl font-bold">${{ product.price }}</p>
        </div>
        <div class="border-2 border-gray-600 w-2/8 text-center py-1 rounded-full font-semibold text-black text-sm">{{ product.category }}</div>
        <div class="flex flex-col">
          <h3 class="font-bold text-black text-xl">Description</h3>
          <p class="font-semibold text-sm text-gray-700">{{ product.description }}</p>
        </div>
        <button @click="mostrarAlerta" class="border-2 bg-black text-white font-semibold text-center py-3 rounded-full cursor-pointer hover:bg-purple-900 transition-colors flex items-center justify-center gap-x-2">
          Buy Now
        </button>
        <div class="flex flex-col gap-y-4">
          <h4 class="font-bold text-black text-xl">Shipping Conditions</h4>
          <div class="grid grid-cols-2 gap-4">
            <div class="flex items-center gap-x-2">
              <div class=" p-2 bg-gray-300 rounded-sm flex items-center justify-center">
                <CirclePercent class="text-black" />
              </div>
              <div class="flex flex-col leading-4">
                <p class="font-semibold text-gray-700 text-sm">Discount</p>
                <p class="text-black font-semibold">No discount</p>
              </div>
            </div>
            <div class="flex items-center gap-x-2">
              <div class=" p-2 bg-gray-300 rounded-sm flex items-center justify-center">
                <Package class="text-black" />
              </div>
              <div class="flex flex-col leading-4">
                <p class="font-semibold text-gray-700 text-sm">Package</p>
                <p class="text-black font-semibold">Regular Package</p>
              </div>
            </div>
            <div class="flex items-center gap-x-2">
              <div class=" p-2 bg-gray-300 rounded-sm flex items-center justify-center">
                <CalendarDays class="text-black" />
              </div>
              <div class="flex flex-col leading-4">
                <p class="font-semibold text-gray-700 text-sm">Delivery Time</p>
                <p class="text-black font-semibold">5 Days</p>
              </div>
            </div>
            <div class="flex items-center gap-x-2">
              <div class=" p-2 bg-gray-300 rounded-sm flex items-center justify-center">
                <Store class="text-black" />
              </div>
              <div class="flex flex-col leading-4">
                <p class="font-semibold text-gray-700 text-sm">Pick up in store</p>
                <p class="text-black font-semibold">Yes</p>
              </div>
            </div>
          </div>
        </div>
        
      </div>
    </div>
  </div>
  
</template>