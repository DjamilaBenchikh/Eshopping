<template>
  <div>
    <header class="top-bar spread" >
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </router-link>
    </nav>
    <div @click="toggleSidebar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>{{totalQuantity}}</span>
    </div>
  </header></div>
  <router-view :inventory="inventory" :addToCart="addToCart" />
  <Sidebar
   v-if="showsidebar"
   :toggle="toggleSidebar"
   :cart="cart"
   :inventory="inventory"
   :remove="removeItem" />
</template>

<style scoped>
</style>
<script>
import Sidebar from '@/components/SidebarComp.vue'
import food from './food.json'
export default {
  components: {
    Sidebar
  },
  data () {
    return {
      showsidebar: false,
      inventory: food,
      cart: {}
    }
  },
  computed: {
    totalQuantity () {
      return Object.values(this.cart).reduce((acc, curr) => {
        return acc + curr
      }, 0)
    }
  },
  methods: {
    addToCart (name, quantity) {
      if (!this.cart[name]) this.cart[name] = 0
      this.cart[name] += quantity
    },
    toggleSidebar () {
      this.showsidebar = !this.showsidebar
    },
    removeItem (name) {
      delete this.cart[name]
    }
  }
}
</script>
