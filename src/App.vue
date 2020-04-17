<template>
  <div id="app">
    <Nav :cart="cart" :premium="premium" />
    <Product :premium="premium" @add-to-cart="updateCart" />
  </div>
</template>

<script>
import Product from "./components/Product";
import Nav from "./components/Nav";

export default {
  name: "App",
  components: {
    Product,
    Nav
  },
  data() {
    return {
      premium: false,
      cart: 0
    };
  },
  methods: {
    updateCart() {
      this.cart += 1;
    }
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
