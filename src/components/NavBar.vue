<template>
    <header id=¨header¨ class="fx-row fx-content-space-between fx-align-items-center">
        <div class="menu container">
            <nav class="navbar">
                <ul class="fx-row fx-align-items-center fx-content-space-between">
                    <li><a @click="router.push({ name: 'Home' })">INICIO</a></li>
                    <li><a @click="router.push({ name: 'Catalog' })">CATALOGO DE PRODUCTOS</a></li>
                </ul>

            </nav>
        </div>

    </header>
  </template>
  
  <script>
    export default {
      name: 'Navbar',
    }
  </script>
  
  <script setup>
    import { onMounted, ref } from "vue";
    import { productsStore } from "@/stores/products";
    import { useRouter } from "vue-router";
  
    const store = productsStore()
    const router = useRouter()
  
    const search = ref('')
  
    const goToProductPage = (id) => {
      router.push({ name: 'ProductView', params: { id } })
    }
    
    onMounted(async () => {
      await store.fetchProductsFromDB()
    })
  </script>
  
  <style scoped>


  
  </style>