<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img  class="logo" src="@/assets/marketicon.png" width="300" height="300" />
    <div >
      <h1 style="font-size:60px; font-weight:900;">Shopping Market</h1>
      <nav style="text-align:center ; width:600px">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/category">Category</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/Testing">Shop</RouterLink>
        
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;

}


nav {
  width: 100%;
  font-size: 30px;
  text-align: center;
  margin-top: 0.5rem;
}

nav a.router-link-exact-active {
  color: black;
}

nav a.router-link-exact-active:hover {
  background-color: black;
  border-radius: 50px;
}

nav a {
  padding: 0 1rem;
  border-left: 1px solid white;
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

 

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;
    background-color: antiquewhite;
    border-radius: 50px;
    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
