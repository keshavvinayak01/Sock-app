<template>
    <form class="review-form" @submit.prevent="onSubmit">
        <p v-if="errors.length">
            <b>Please correct the following error(s):</b>
            <ul>
                <li v-for="error in errors" :key="error">{{ error }}</li>
            </ul>
        </p>
        <p>
            <label for="name">Name:</label>
            <input id="name" v-model="name" placeholder="Name">
        </p>
        <p>
            <label for="review">Review:</label>
            <textarea id="review" v-model="review" />
        </p>
        <p>
            <label for="rating">Rating:</label>
            <select id="rating" v-model.number="rating">
                <option >5</option>
                <option >4</option>
                <option >3</option>
                <option >2</option>
                <option >1</option>
            </select>
        </p>
        <p>
            <input type="submit" value="Submit">
        </p>
    </form>
</template>

<script>
import { eventBus } from '../main'
export default {
  name: 'ProductReviewComponent',
  methods : {
      onSubmit() {
          if(this.name && this.review && this.rating) {
              let productReview = {
              name : this.name,
              review : this.review,
              rating : this.rating
            }
            eventBus.$emit(
              'review-submitted',
              productReview
            )
            this.name = null
            this.review = null
            this.rating = null
          }
        else {
            if(!this.name) this.errors.push("Name required.")
            if(!this.review) this.errors.push("Review required.")
            if(!this.rating) this.errors.push("Rating required.")
        }
          
      }
  },
  computed : {
  },
  data () {
    return {
        name : null,
        review : null,
        rating : null,
        errors : []
    }
  }
}
</script>