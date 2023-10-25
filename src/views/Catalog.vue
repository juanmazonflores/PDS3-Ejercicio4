<template>
  <div class="products-list">
    <v-row no-gutters>
      <v-col
          v-for="product in store.products"
          :key="product.id"
          cols="3"
          sm="4"
          @click="goToProductPage(product.id)">
        <product-item
            :product-data="product"
            @item-clicked="goToProductPage"/>
      </v-col>
    </v-row>
    </div>
</template>

<script>
  import { defineComponent } from "vue";
  import ProductItem from "@/components/ProductItem.vue";
  export default defineComponent({
    name: 'CatalogView',
    components: {
      ProductItem
    }
  })
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
  .card{
 background-color: var(--color-container);
 color: var(--color-font3);
}

.product{
 background-color: var(--color-container2);
}
</style>

