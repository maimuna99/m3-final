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
    const res = await fetch('https://dummyjson.com/products/')
    console.log(res)
    response.value = (await res.json())
  } catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
  }

</script>
<template >

  
<select  v-model="SelectedProduct" >
<option>smartphones</option>
<option>laptops</option>
<option>fragrances</option>
<option>skincare</option>
<option>groceries</option>
<option>home-decoration</option>
</select>
<div  class="card" v-for="product in response.products" :key="product.id" > 
    <b>{{ product.title }} </b><hr/> 
    <!-- <b>Description: </b>{{product.description}}<br/> -->
    <b>Price: </b>{{product.price}} OMR<br/>
    <!-- <b>Discount percentage: {{product.discountPercentage}}%<br/></b>
    <b>Category:{{product.category}}</b> -->
    <img class='cardimg' :src=product.thumbnail alt="Avatar" style="width:100%">
    <div style="text-align:center">
        <b>Rating: </b>{{product.rating}}/5<br/>
        <span v-if="product.rating >= 5">⭐ ⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 4">⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 3">⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 2">⭐ ⭐</span>
        <span v-else>⭐</span><br/>
        
        <!-- <button v-model="SelectedProduct">View Details</button> -->
    </div>
    <Listing :product="SelectedProduct"/>
   
</div>
<!-- <p class="card" v-for="product in response.products" :key="product.id">
    {{ product.title }}</p> -->
</template>
<style>

.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  width: 20rem;
  padding:10px;
  margin:10px;
  color:black;
  text-align:left;
  background-color:grey;
}
</style>