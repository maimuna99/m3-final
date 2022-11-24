<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img   src="@/assets/marketicon.png" width="350" height="350" />
<div></div>
    <div class="wrapper">
      <HelloWorld msg="Shopping Market" />

      <nav>
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
  font-size: 12px;
  text-align: center;
  margin-top: 1rem;
}

nav a.router-link-exact-active {
  color: var(#540b0e);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(#540b0e;);
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



  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 2rem;

  }
}
</style>
