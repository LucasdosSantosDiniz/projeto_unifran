<template>
  <div>
    <Banner/>
    <div class="container">
      <h1> Pedidos</h1>
      <Dashboard/>
   </div>
  </div>
</template>
<script>
import Dashboard from '../components/Dashboard.vue';
import Banner from "../components/Banner.vue";
export default {
  name:"Pedidos",
  components:{
    Dashboard,
    Banner,
  }
}
</script>
