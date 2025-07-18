<script setup>
defineProps({
  product: Object
})
</script>

<template>
  <router-link to="/">
    <h2>{{ product.title }}</h2>
    <p>{{ product.price }}</p>
  </router-link>
</template>