<script setup>
import Product from '../components/Product.vue'
const { id } = defineProps(['id']);
</script>

<template>
    <Suspense>
      <Product :id="id"/>
    </Suspense>
    
  </template>