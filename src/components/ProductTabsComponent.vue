<template>
  <div>
      <span 
      class="tab"
      v-for="(tab, index) in tabs" :key="index" >
        {{ tab }}
      </span>
  </div>
</template>

<script>
export default {
  name: 'ProductTabsComponent',
  components: {
  },
  data() {
    return {
        tabs : ['Reviews', 'Make a review']
    }
  },
  methods : {
  }
}
</script>