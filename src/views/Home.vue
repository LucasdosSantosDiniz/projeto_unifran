<template>
  <div>
    <Banner/>
    <div class="container">
        <h1>Monte seu Hamburguer</h1>
        <Form />
    </div>  
  </div>
</template>

<script>
import Banner from "../components/Banner.vue";
import Form from "../components/Form.vue";

export default{
  name:"Home",
  components:{
    Banner,
    Form
  }
}
</script>
