<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo" />
    </router-link>
    <h2>OASIS BURGERS</h2>
    <router-link to="/">Home</router-link> |
    <router-link to="/pedidos">Pedidos</router-link>
  </div>
</template>
<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"],
};
</script>
<style scoped>
#nav {
  background-color: #e70f0f;
  border-bottom: #e70f0f;
  padding: 15px 50px;
  display: flex;
  font-weight: bolder;
  justify-content: flex-end;
  align-items: center;
  position: fixed;
  top: 0;
  width: 100%;
}

#nav a {
  color: #fcba03;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
}

#nav a:hover {
  color: #fff;
}

#nav #logo-url {
  margin: auto;
  margin-left: 0;
}

#logo {
  width: 70px;
  height: 60px;
}

h2 {
  color: red;
  margin-right: 500px;
  background: yellow;
}
</style>