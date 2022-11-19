<template>
  <div>
    <Navbar :logo="src_logo" :alt="app_name" />
    <router-view/>    
    <Footer :logo="src_logo" :alt="app_name"/>
  </div>
</template>
<script>
import Navbar from './components/Navbar.vue';
import Footer from "./components/Footer.vue";
export default {
  components:{
    Navbar,
    Footer
  },
  data() {
      return {
        src_logo:"/img/oasis-burgers.png",
        app_name:"Oasis Burguers"
      };
  },
}
</script>
<style>
*{
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.container {
  margin: 50px;
  min-height: 250px;
}
h1{
  text-align: center;
  font-size: 42px;
  margin-bottom:30px;
  color: black;
}
</style>
