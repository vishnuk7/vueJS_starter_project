<template>
  <div class="product">
    <div class="product-image">
      <img :src="img" :alt="product" />
    </div>
    <div class="product-info">
      <h5>{{ product }}</h5>
      <p>{{ description }}</p>
      <ul>
        <li v-for="detail in details" :key="detail">{{ detail }}</li>
      </ul>
      <div v-for="variant in variants" :key="variant.variantId">
        <p>{{ variant.variantColor }}</p>
      </div>
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
      <p>Cart: {{ cart }}</p>
      <button @click="addToCart">Add to Cart</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Product",
  data() {
    return {
      product: "Scoks",
      description: "A pair of warm, fuzzy socks",
      img: "../assets/scocks-1.jpeg",
      isStock: true,
      cart: 0,
      details: ["80% cotton", "20% polyester", "Gender-neutral"],
      variants: [
        {
          variantId: 3334,
          variantColor: "green"
        },
        {
          variantId: 3335,
          variantColor: "blue"
        }
      ]
    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  width: 450px;
}
</style>
