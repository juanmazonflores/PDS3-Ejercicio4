<template>
  <header>
    <nav-bar></nav-bar>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<script setup>
  import { useRouter } from "vue-router";
  import { productsStore } from "@/stores/products";
  import NavBar  from "./components/NavBar.vue";

  const router = useRouter()
  const store = productsStore()
</script>


<style>
@import  "./assets/styles.css";
</style>
