<template>
  <Products />
</template>

<script>
import Products from "./components/products/Products.vue";

export default {
  name: "App",
  components: {
    Products,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
