<template>
  <div id="app">
    <Nav :cart="cartLength" :premium="premium" />
    <Product :premium="premium" :reviews="reviews" @add-to-cart="updateCart" />
    <ProductReview @review-submitted="addReview" />
  </div>
</template>

<script>
import Product from "./components/Product";
import Nav from "./components/Nav";
import ProductReview from "./components/ProductReview";

export default {
  name: "App",
  components: {
    Product,
    Nav,
    ProductReview
  },
  data() {
    return {
      premium: false,
      cart: [],
      cartLength: 0,
      reviews: []
    };
  },
  methods: {
    updateCart(id) {
      this.cart.push(id);
      this.cartLength = this.cart.length;
    },
    addReview(productReview) {
      this.reviews.push(productReview);
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
