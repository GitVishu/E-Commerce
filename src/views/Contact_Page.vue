<template>
  <Navbar/>
  <Contact_Us class="bg"/>
 <MainFooter/>

</template>

<script>

import Navbar from "../components/Navbar.vue";
import Contact_Us from "../components/Contact_Us.vue";
import MainFooter from "../components/MainFooter.vue";

export default{
  components:{
    Navbar,
    Contact_Us,
    MainFooter
  }
}
</script>
<style scoped>
.bg{
  background-color:#e6e6fa
}
</style>

