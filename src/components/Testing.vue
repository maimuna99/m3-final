<script setup>
	import { ref } from 'vue';
    import Listing from "./Listing.vue";
	const response = ref({});
  const SelectedProduct = ref(null);
  const cartList = ref([]);



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
 
  
      <a href="#" id="cart"><i class="fa fa-shopping-cart" style="margin-top: 220px; font-size: 30px;"></i> Cart <span class="badge" >{{cartList.length}}</span></a>


<!-- <div style="background-color:whitesmoke; margin-left: 10px; width:300px; margin-top: 50px;padding:15px; height:50px; ">
  Shopping Cart <hr/>
  <span v-for="product in cartList" :key="product.id">
    {{product}}<br/>
  </span>
</div> -->

    <!-- <br />
    <br />
    <div v-for="product in response.products"
      :value="product.title"
      :key="product.id"
      class="select">
    <input type="checkbox" id="option1"
    :value="product.title"
    v-model="cartList" />
    <label for="option1">{{ product.title }}</label>
    </div> -->
    
<div  class="card" v-for="product in response.products" :key="product.id" > 
    <b>{{ product.title }} </b><hr/> 
    <!-- <b>Description: </b>{{product.description}}<br/> -->
    <b>Price: </b>{{product.price}} OMR<br/>
    <!-- <b>Discount percentage: {{product.discountPercentage}}%<br/></b>
    <b>Category:{{product.category}}</b> -->
    <img class='cardimg' :src=product.thumbnail alt="Avatar" style="width:100%">
    <div style="text-align:center">
        <b>Rating: </b>{{product.rating}}/5<br/>
        <span v-if="product.rating >= 4.5">⭐ ⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 3.5">⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 2.5">⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 1.5">⭐ ⭐</span>
        <span v-else>⭐</span><br/>
        <input type="checkbox" id="option1"
        :value="product.title"
        v-model="cartList" />Add To Cart
        <!-- <button v-model="SelectedProduct">View Details</button> -->
    </div>
    <RouterLink :to="{name:'product', params:{id:product.id}}"><button>View Details</button> </RouterLink>
    <!-- <Listing :product="SelectedProduct"/> -->
   
</div>
<!-- <p class="card" v-for="product in response.products" :key="product.id">
    {{ product.title }}</p> -->
</template>
<style>


@import url(https://fonts.googleapis.com/css?family=Lato:300,400,700);

@import url(https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css);





.lighter-text {
  color: #ae3a3a;
}



nav {
  padding: 10px;
  background: #F8F8F8;
  font-size: 16px;}
  
 
  
  .navbar-right {
    float: right;
  }



.badge {
    border-radius: 10px;
    color: white;
    display: inline-block;
    font-size: 12px;
    line-height: 1;
    padding: 3px 7px;
    text-align: center;
    vertical-align: middle;
    white-space: nowrap;
}

.shopping-cart {
  margin: 20px ;
  float: right;
  background: white;
  width: 320px;
  position: relative;
  border-radius: 3px;
  padding: 20px;}
  
  
  .shopping-cart-header {
    border-bottom: 1px solid #E8E8E8;
    padding-bottom: 15px;}
    
    .shopping-cart-total {
      float: right;
    }
  
  
  

    img {
      float: left;
      margin-right: 12px;
    }
    
    .item-name {
      display: block;
      padding-top: 10px;
      font-size: 16px;
    }
    



.shopping-cart:after {
	bottom: 100%;
	left: 89%;
	border: solid transparent;
	content: " ";
	height: 0;
	width: 0;
	position: absolute;
	pointer-events: none;
	border-bottom-color: white;
	border-width: 8px;
	margin-left: -8px;
}

.cart-icon {
  color: #515783;
  font-size: 24px;
  margin-right: 7px;
  float: left;
}




.clearfix:after {
  content: "";
  display: table;
  clear: both;
}



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

.card:hover {
  box-shadow: 0 8px 16px 0 hwb(0 75% 11% / 0.2);
}


</style>