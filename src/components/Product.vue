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
      <div class="color-option">
        <div
          class="color-box"
          v-for="variant in variants"
          :key="variant.variantId"
          :style="{ backgroundColor: variant.variantColor }"
          @mouseover="updateProduct(variant.variantImg)"
        ></div>
      </div>
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
      <p>Cart: {{ cart }}</p>
      <button
        @click="addToCart"
        :disabled="!inStock"
        :class="{ disabledButton: !inStock }"
      >Add to Cart</button>
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
      inStock: false,
      cart: 0,
      details: ["80% cotton", "20% polyester", "Gender-neutral"],
      variants: [
        {
          variantId: 3334,
          variantColor: "lightgreen",
          variantImg: "../assets/scocks-1.jpeg"
        },
        {
          variantId: 3335,
          variantColor: "lightblue",
          variantImg: "../assets/scocks-2.jpeg"
        }
      ]
    };
  },
  methods: {
    addToCart() {
      this.cart += 1;
    },
    updateProduct(variantImg) {
      this.img = variantImg;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  width: 450px;
}

.color-option {
  display: flex;
}

.color-box {
  width: 50px;
  height: 50px;
  background-color: ;
}
</style>
