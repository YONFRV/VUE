<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Nav from './components/Nav.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <Nav></Nav>
  <div class="container-fluid mt-3 ">
    <RouterView />  
  </div> 
  <Footer></Footer>
</template>
