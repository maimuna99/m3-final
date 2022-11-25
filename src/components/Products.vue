<script setup>
	import { ref } from 'vue'
	const response = ref({})
  const prod = toRef(props, 'id');

  // adding delay
  await new Promise(resolve => {
    setTimeout(() => { 
      resolve()
    }, 1000)
  })
    
  try {
    const res = await fetch('https://dummyjson.com/products/' +  Math.floor(Math.random() * 10)+1)
    console.log(res)
    response.value = (await res.json())
  } catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
  }

</script>

<template >
  <div class="card"> 
    <b>{{ prod.title }} </b><hr/> 
    <b>Description: </b>{{prod.description}}<br/>
    <b>Price: </b>{{prod.price}} OMR<br/>
    <b>Discount percentage: {{prod.discountPercentage}}%<br/></b>
    <b >Category: </b> {{prod.category}}
    <img class='cardimg' :src=prod.thumbnail alt="Avatar" style="width:100%">
    <b>Rating: </b>{{prod.rating}}/5
  </div>

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
  background-color:beige;
}
</style>