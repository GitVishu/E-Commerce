<template>
  <div class="bg">
    <div><Navbar /></div>
    <div><HeroSection /></div>
    <About/>

    <div><Contact_Us /></div>
    <MainFooter/>
    
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import HeroSection from "../components/HeroSection.vue";
import About from "../components/About_Us.vue";
import Contact_Us from "../components/Contact_Us.vue";
import MainFooter from "../components/MainFooter.vue"

export default {
  components: {
    Navbar,
    HeroSection,
    About,
    Contact_Us,
    MainFooter
  },
};
</script>
<!-- <style >
.bg{
  background-color:#e6e6fa
}</style> -->
