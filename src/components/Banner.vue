<template>
  <div id="banner"></div>
</template>
<script>
export default {
  name: "Banner",
};
</script>
<style scoped>
#banner {
  background-image: url("/public/img/banner.jpg");
  background-position: 0 -250px;
  background-size: cover;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}
</style>