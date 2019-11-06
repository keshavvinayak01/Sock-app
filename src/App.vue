<template>
  <div>
    <div class="nav-bar"></div>
    <div id="app">
      <div class="cart">
        <p>Cart({{cart.length}})</p>
      </div>
      <HomeComponent 
      product = "Socks"
      :premium = false
      @add-to-cart="updateCart"
      />
    </div>
  </div>
</template>

<script>
import HomeComponent from './components/HomeComponent.vue'
import './styles/main.css'
export default {
  name: 'app',
  components: {
    HomeComponent
  },
  data() {
    return {
      cart : []
    }
  },
  methods : {
    updateCart(id) {
      this.cart.push(id)
    }
  }
}
</script>

<style>
</style>
