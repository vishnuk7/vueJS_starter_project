<template>
  <div id="app">
    <Product :premium="premium" />
  </div>
</template>

<script>
import Product from "./components/Product";

export default {
  name: "App",
  components: {
    Product
  },
  data() {
    return {
      premium: false
    };
  }
};
</script>

<style>
*,
*::before,
*::after {
  padding: 0;
  margin: 0;
  box-sizing: inherit;
}

html {
  box-sizing: border-box;
}

body {
  font-family: sans-serif;
}
</style>
