<script setup>
	import { ref } from 'vue';
	const response = ref({});

  let imges = document.images
let primary = document.getElementById("primary")

for(let i = 0; i<imges.length; i++){
   imges[i].addEventListener("click",changeImage)
}

function changeImage(event){
  console.log(event.target)
}

    const { id } = defineProps(['id']);
    //const prod = toRef(props, 'id');
    
    
    
   
  try {
    const res = await fetch('https://dummyjson.com/products/'+ id)
    console.log(res)
    response.value = (await res.json())
  } catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
  }

</script>
<template>
  <div class="wrapper" style="background-color:whitesmoke;">
    <h1 style="font-weight:900; align-content: center;">{{ response.title }}</h1>
    <div style="background-color:whitesmoke; height: 50px;text-align:right;">
        <b>Rating: </b>{{response.rating}}/5
        <span v-if="response.rating >= 4.5">⭐ ⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 3.5">⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 2.5">⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 1.5">⭐ ⭐</span>
        <span v-else>⭐</span><br/>
      </div>
    <div class="product-img">
      <img :src=response.thumbnail height="420" width="327">
    </div>
    <div class="product-info">
      <div class="product-text" style="padding-top: 30px; width:100%; height: 200px;">
        <h2 style="color:black; font-size:20px"><b style="font-weight:800; color: darkred;">Category: </b>{{response.category}}</h2>
        <p style="color:black; font-size:20px"><b style="font-weight:800; color: darkred;">Product Description: </b>{{response.description}} <br/>
        <b style="font-weight:800; color: darkred;">Price: </b>{{response.price}} OMR <br/>
        <b style="font-weight:800; color: darkred;">Discount: </b>{{response.discountPercentage}}<br/>
        <b style="font-weight:800; color: darkred;">Brand: </b>{{response.brand}} OMR <br/>
        </p>
      </div>
      
      <div style="margin-top:100px; margin-left: 130px;"><img id="img2" :src=response.images[1] class="tumbs">
<img id="img3" :src=response.images[2] class="tumbs">
<img id="img4" :src=response.images[3] class="tumbs">
    </div>
  </div> </div>

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
@import url(https://fonts.googleapis.com/css?family=Dosis:300,400);


@import url(https://fonts.googleapis.com/css?family=Lato:300,400,700);

@import url(https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css);





.lighter-text {
  color: #ae3a3a;
}
.tumbs{
  height:100px;
  margin:3px;
  cursor:pointer;
  opacity:0.8;
}

.tumbs:hover{
  opacity:1;
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
  width: 1054px;
  margin-left: 200px;
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
  width: 727px;
  border-radius: 0 7px 10px 7px;
  background-color: #ffffff;
}

.product-text {
  height: 300px;
  width: 327px;
  padding-left: 100px;
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