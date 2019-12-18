<template>
  <div id="app">
    <ProductBuilder />
  </div>
</template>

<script>
import ProductBuilder from "./components/ProductBuilder";
export default {
  name: "app",
  components: {
    ProductBuilder
  }
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
