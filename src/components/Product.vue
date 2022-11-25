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

    {{response.title}}
    <!-- <div  class="card"  > 
    <b>{{ response.title }} </b><hr/> 
    <b>Description: </b>{{response.description}}<br/>
    <b>Price: </b>{{response.price}} OMR<br/>
    <b>Discount percentage: {{response.discountPercentage}}%<br/></b>
    <b>Category:{{response.category}}</b>
    <img class='cardimg' :src=response.thumbnail alt="Avatar" style="width:100%">
    <div style="text-align:center">
        <b>Rating: </b>{{response.rating}}/5<br/>
        <span v-if="response.rating >= 4.5">⭐ ⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 3.5">⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 2.5">⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 1.5">⭐ ⭐</span>
        <span v-else>⭐</span><br/>
    </div>
   
</div> -->
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