<template>
  <div class="product">
    <div class="product-image">
      <img v-bind:src="image" />
    </div>
    <div class="product-info">
      <h1>{{ product }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeComponent',
  props: {
    product: String,
  },
  data : function() {
    return {
      image : "https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg"
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
