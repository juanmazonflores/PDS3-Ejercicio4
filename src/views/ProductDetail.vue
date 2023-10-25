<template>

  <v-btn
      @click="router.push({ name: 'Catalog' })"
      color="primary"
      variant="elevated">
    Regresar al Catalogo
  </v-btn>

  <div class="product">
    <div class="product-image">
      <img :src="selectedProduct.thumbnail" alt="">
    </div>
    <div class="product-details">
      <p>Brand: {{ selectedProduct.brand }}</p>
      <p>Description: {{ selectedProduct.description }}</p>
      <h2>Price: ${{ selectedProduct.price }}</h2>
    </div>
  </div>
</template>


<script>
  import { defineComponent } from "vue";
  export default defineComponent({
    name: 'ProductDetails'
  })
</script>

<script setup>
  import { computed } from "vue";
  import { productsStore } from "@/stores/products";
  import { useRoute, useRouter } from "vue-router";

  const store = productsStore()
  const router = useRouter()
  const route = useRoute()

  const selectedProduct = computed(() => {
    return store.products.find((item) => item.id === Number(route.params.id))
  })

</script>

<style scoped>
.product {
  display: flex;
  margin-top: 50px;
  color: var(--color-font3);
  background-color: var(--color-container2);
}

.product-image {
  margin-right: 24px;
}

</style>