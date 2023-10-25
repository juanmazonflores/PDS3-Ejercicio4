<template>
    <section id="home" class="scene">
        <div class="home-banner fx-row fx-column-responsive fx-align-items-center fx">
            <div class="home-descripcion">
                <h1>CATALOGO DE PRODUCTOS</h1>
                <p>Bienvenido al catalogo de productos
                </p>
                <v-btn
                @click="router.push({ name: 'Catalog' })"
                color="primary"
                variant="elevated">
                Ver catalogo
                </v-btn>
            </div>
            
        </div>
    </section>

</template>

<script setup>
  import { useRoute, useRouter } from "vue-router";

  const router = useRouter()
  const route = useRoute()

</script>
