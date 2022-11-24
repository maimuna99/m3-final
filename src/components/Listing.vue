<script setup>
import { toRef } from "vue";
const props = defineProps(["product"]);
const Product = toRef(props, "product");
</script>
<template>
  {{ Product }}



</template>