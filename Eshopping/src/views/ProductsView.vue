<template>
 <main class="wrapper">
   <h1>Products</h1>
   <div class="card-container">
   <ProductCart
     v-for="(product, i) in inventory"
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
import ProductCart from '@/components/ProductCart.vue'
export default {
  props: ['inventory', 'addToCart'],
  components: {
    ProductCart
  }
}
</script>
