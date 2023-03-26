<template>
  <div class="home">
  </div>
    <div class="splash-container">
        <div class="splash">
        
        </div>
 </div>
    <main class="wrapper">
        <h2>Recommended</h2>
        <div class="recommended">
        <ProductCart
          v-for="(product, i) in inventory.slice(0,3)"
          :key="product.id"
          class="card"
          :i='i'
          :product="product"
          :addToCart="addToCart"
        />
        </div>
      </main>
</template>
<script>
// @ is an alias to /src
import ProductCart from '@/components/ProductCart.vue'
export default {
  name: 'HomeView',
  props: ['inventory', 'addToCart'],
  components: {
    ProductCart
  }
}
</script>
