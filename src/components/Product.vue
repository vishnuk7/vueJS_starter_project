<template>
  <div class="product">
    <div class="product-image">
      <img :src="image" :alt="product" />
    </div>
    <div class="product-info">
      <h5>{{ title }}</h5>
      <p>{{ description }}</p>
      <ul>
        <li v-for="detail in details" :key="detail">{{ detail }}</li>
      </ul>
      <div class="color-option">
        <div
          class="color-box"
          v-for="(variant,index) in variants"
          :key="index"
          :style="{ backgroundColor: variant.variantColor }"
          @mouseover="updateProduct(index)"
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
      brand: "Viu",
      description: "A pair of warm, fuzzy socks",
      selectedVariant: 0,
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
    updateProduct(index) {
      this.selectedVariant = index;
      console.log(this.selectedVariant);
    }
  },
  computed: {
    title() {
      return this.brand + " " + this.product;
    },
    image() {
      return this.variants[this.selectedVariant].variantImg;
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
