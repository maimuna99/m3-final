<script setup>
	import { ref } from 'vue';
	const response = ref({});



    const { id } = defineProps(['id']);

  try {
    const res = await fetch('https://dummyjson.com/products/'+ id)
    console.log(res)
    response.value = (await res.json())
  } catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
  }

</script>
<template>
    
    {{response}}
</template>