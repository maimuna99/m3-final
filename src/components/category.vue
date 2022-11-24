<script setup>
	import { ref } from 'vue';
    import Listing from "./Listing.vue";
	const response = ref({});
    const SelectedProduct = ref(null);

  // adding delay
await new Promise(resolve => {
    setTimeout(() => {
        resolve()
    }, 1000)
})
    
try {
    const res = await fetch('https://dummyjson.com/products')
    //console.log(res)
    response.value = (await res.json())
} catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
}
console.log(response)
</script>
<template > 
<button>{{response.product}} </button>

</template>
