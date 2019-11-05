<template>
  <div>
    <div class="nav-bar"></div>
    <div id="app">
      <HomeComponent 
      product="Henlo"
      image = "../assets/green-sock.jpg"
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
  }
}
</script>

<style>
</style>
