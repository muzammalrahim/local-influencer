<template>
  <NavBar />
  <MainContent />
  <Footer />
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import MainContent from './components/MainContent.vue'
import Footer from './components/Footer.vue'
import axios from 'axios'

export default {
  data() {
    return {
      compaign:[],
    }
  },
  mount() {
     
  }
}
</script>

<style>

</style>