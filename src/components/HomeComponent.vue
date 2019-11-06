<template>
  <div class="product">
    <div class="product-image">
      <img v-bind:src="image" />
    </div>
    <div class="product-info">
      <h1>{{ title }}</h1>
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
      <p>Shipping : {{shipping}}</p>
      <ul>
        <li v-for='detail in details' :key="detail"> {{detail}} </li>
      </ul>
      <div 
      v-for="(variant, index) in variants" 
      :key="variant.variantId"
      class="color-box"
      :style="{ backgroundColor : variant.variantColor }"
      @mouseover="updateProduct(index)" >
      </div>
      <button 
      v-on:click="addToCart" 
      :disabled="!inStock"
      :class="{ disabledButton : !inStock }" >Add to Cart</button>
      <ProductTabsComponent :reviews="reviews" />
    </div>
    
  </div>
</template>

<script>
import ProductTabsComponent from './ProductTabsComponent'
import eventBus from './eventBus'
export default {
  name: 'HomeComponent',
  components : {
    ProductTabsComponent
  },
  props: {
    premium : Boolean,
    product: String,
  },
  methods : {
    addToCart() {
      this.$emit('add-to-cart', this.variants[this.selectedVariant].variantId)
    },
    updateProduct(index) {
      this.selectedVariant = index
    }
  },
  computed : {
    shipping() {
      if(this.premium) {
        return "free"
      }
      else{
        return "2.99"
      }
    },
    title() {
      return this.brand + ' ' + this.product
    },
    image(){
      return this.variants[this.selectedVariant].variantImage
    },
    inStock() {
      return this.variants[this.selectedVariant].variantQuantity
    }
  },
  mounted(){
    eventBus.$on('review-submitted', productReview => {
      productReview.id = this.reviews.length
      this.reviews.push(productReview)
    })
  },
  data () {
    return {
      brand : 'Vue Mastery',
      reviews : [],
      selectedVariant : 0,
      details : ["90% cotton", "20% polyester", "Gender-neutral"],
      variants : [
        {
          variantId : 2234,
          variantColor : "green",
          variantImage : "https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg",
          variantQuantity : 10
        },  
        {
          variantId : 2235,
          variantColor : "blue",
          variantImage : "https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg",
          variantQuantity : 0
        }
      ],
    }
  }
}

</script>