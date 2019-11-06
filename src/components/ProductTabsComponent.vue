<template>
  <div>
      <span 
      class="tab"
      :class="{ activeTab: selectedTab === tab}"
      v-for="(tab, index) in tabs" 
      :key="index"
      @click="selectedTab = tab" >
        {{ tab }}
      </span>
      <div v-show="selectedTab === 'Reviews'">
      <p v-if="!reviews.length">There are no reviews yet.</p>
      <ul v-else>
        <li v-for="review in reviews" :key="review.id">
          <p> {{ review.name }} </p>
          <p> Rating : {{ review.rating }} </p>
          <p> {{ review.review }} </p>
        </li>
      </ul>
    </div>
    <ProductReviewComponent 
    v-show="selectedTab === 'Make a review'" /> 
  </div>
</template>

<script>
import ProductReviewComponent from './ProductReviewComponent'
export default {
  name: 'ProductTabsComponent',
  props : {
      reviews : Array
  },
  components: {
      ProductReviewComponent
  },
  data() {
    return {
        tabs : ['Reviews', 'Make a review'],
        selectedTab : 'Reviews'
    }
  },
  methods : {
  }
}
</script>