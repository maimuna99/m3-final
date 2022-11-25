<script setup>
	import { ref } from 'vue';
    import Listing from "./Listing.vue";
	const response = ref({});
  const SelectedProduct = ref(null);
  const cartList = ref([]);

//   (function(){
 
//  $("#cart").on("click", function() {
//    $(".shopping-cart").fadeToggle( "fast");
//  });
 
// })();

  try {
    const res = await fetch('https://dummyjson.com/products/')
    console.log(res)
    response.value = (await res.json())
  } catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
  }

 

</script>
<template >
 

  <nav>
  <div class="container" style="height: 30px;">
    <div class="navbar-right" >
      <a href="#" id="cart" style="margin-right:50px; padding-bottom: 20px;"><i class="fa fa-shopping-cart" ></i>   My Cart   <span class="badge" style="background-color:#540b0e;">{{cartList.length}}</span></a>
    </div> <!--end navbar-right -->
  </div> <!--end container -->

</nav>

<div class="container" style="z-index: 999;position: right;background-color: #edede9;">
  <div class="shopping-cart" style="background-color: #edede9; box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);">
    <div class="shopping-cart-header">
      <div class="shopping-cart-total">
        <span class="lighter-text">Total Items:</span>
        <span class="main-color-text">{{cartList.length}}</span><hr/>

    <ul  v-for="product in cartList" :key="product.id">
      <li >
        <img  :src=product.thumbnail height="40" width="40" alt="item" />
        <span style="font-size:20px;">{{ product.title }}</span><br/>
        <span style="font-size:20px;">Price:{{product.price}} OMR</span><hr/>
      </li>
      
    </ul>
      </div>
    </div> <!--end shopping-cart-header -->
  </div> <!--end shopping-cart -->
</div> <!--end container -->


<div class="shop">
  <div v-for="product in response.products" :key="product.id" style="padding:20px;"> 
  <div class="wrapper">
    <div class="product-img">
      <img :src=product.thumbnail height="420" width="327">
    </div>
    <div class="product-info">
      <div class="product-text">
        <h1>{{ product.title }}</h1>
        <h2>Category:{{product.category}}</h2>
        <p>{{product.description}} </p>
      </div>
      <input type="checkbox" id="option1"  :value="product"  v-model="cartList" style="margin-left:40px;" />Add To Cart
      <div class="product-price-btn">
        <p><span> Price:{{product.price}} OMR</span></p>
        <RouterLink :to="{name:'product', params:{id:product.id}}"><button style="margin-top: 40px;" >View Details</button> </RouterLink>
      </div>
    </div>
  </div>
</div></div>
  <!-- <div  class="card" v-for="product in response.products" :key="product.id" > 
    <b>{{ product.title }} </b><hr/> 
    <b>Description: </b>{{product.description}}<br/> 
    <b>Price: </b>{{product.price}} OMR<br/>
     <b>Discount percentage: {{product.discountPercentage}}%<br/></b>
    <b>Category:{{product.category}}</b> 
    <img class='cardimg' :src=product.thumbnail alt="Avatar" style="width:100%">
    <div style="text-align:center">
        <b>Rating: </b>{{product.rating}}/5<br/>
        <span v-if="product.rating >= 4.5">⭐ ⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 3.5">⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 2.5">⭐ ⭐ ⭐</span>
        <span v-else-if="product.rating >= 1.5">⭐ ⭐</span>
        <span v-else>⭐</span><br/>
        <input type="checkbox" id="option1"
        :value="product"
        v-model="cartList" />Add To Cart
    </div>
    <RouterLink :to="{name:'product', params:{id:product.id}}"><button>View Details</button> </RouterLink>
   
</div> 

  </div>  -->
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
    font-size: 12px;
    padding: 3px 7px;
    text-align: center;
    vertical-align: middle;

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
  color: #540b0e;
  font-size: 24px;
  margin-right: 7px;
  float: left;
}




.clearfix:after {
  content: "";
  display: table;
  clear: both;
}



 .shop {
    display: grid;
    margin-top: 100px;
    align-self: right;
    grid-template-columns:  3fr 1fr;
    padding: 0 2rem;
  } 


  .wrapper {
  height: 420px;
  width: 654px;
  margin: 50px auto;
  border-radius: 7px 7px 7px 7px;
  /* VIA CSS MATIC https://goo.gl/cIbnS */
  -webkit-box-shadow: 0px 14px 32px 0px rgba(0, 0, 0, 0.15);
  -moz-box-shadow: 0px 14px 32px 0px rgba(0, 0, 0, 0.15);
  box-shadow: 0px 14px 32px 0px rgba(0, 0, 0, 0.15);
}

.product-img {
  float: left;
  height: 420px;
  width: 327px;
}

.product-img img {
  border-radius: 7px 0 0 7px;
}

.product-info {
  float: left;
  height: 420px;
  width: 327px;
  border-radius: 0 7px 10px 7px;
  background-color: #ffffff;
}

.product-text {
  height: 300px;
  width: 327px;
}

.product-text h1 {
  margin: 0 0 0 38px;
  padding-top: 52px;
  font-size: 34px;
  color: #474747;
}

.product-text h1,
.product-price-btn p {
  font-family: 'Bentham', serif;
}

.product-text h2 {
  margin: 0 0 47px 38px;
  font-size: 13px;
  font-family: 'Raleway', sans-serif;
  font-weight: 400;
  text-transform: uppercase;
  color: #d2d2d2;
  letter-spacing: 0.2em;
}

.product-text p {
  height: 125px;
  margin: 0 0 0 38px;
  font-family: 'Playfair Display', serif;
  color: #8d8d8d;
  line-height: 1.7em;
  font-size: 15px;
  font-weight: lighter;
  overflow: hidden;
}

.product-price-btn {
  height: 103px;
  width: 327px;
  margin-top: 17px;
  position: relative;
}

.product-price-btn p {
  display: inline-block;
  position: absolute;
  top: -13px;
  height: 50px;
  font-family: 'Trocchi', serif;
  margin: 0 0 0 38px;
  font-size: 28px;
  font-weight: lighter;
  color: #474747;
}

span {
  display: inline-block;
  height: 50px;
  font-family: 'Suranna', serif;
  font-size: 34px;
}

.product-price-btn button {
  display: inline-block;
  height: 50px;
  width: 176px;
  margin: 0 40px 0 16px;
  box-sizing: border-box;
  border: transparent;
  border-radius: 60px;
  font-family: 'Raleway', sans-serif;
  font-size: 14px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: #ffffff;
  background-color: #9cebd5;
  cursor: pointer;
  outline: none;
}

.product-price-btn button:hover {
  background-color: #79b0a1;
}

</style>