<template>
  <div class="product">
    <div class="product-image">
      <img :src="image" :alt="product" />
    </div>
    <div class="product-info">
      <h5>{{ title }}</h5>
      <p class="desc">{{ description }}</p>
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
      <small v-if="inStock">
        In Stock
        <span class="bold">{{ shipping }}</span>
      </small>
      <small v-else>Out of Stock</small>

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
  props: {
    premium: {
      type: Boolean,
      required: true
    }
  },
  data() {
    return {
      product: "Scoks",
      brand: "Viu",
      description: "A pair of warm, fuzzy socks",
      selectedVariant: 0,
      details: ["80% cotton", "20% polyester", "Gender-neutral"],
      variants: [
        {
          variantId: 3334,
          variantColor: "#2a8351",
          variantImg: "../assets/scocks-1.jpeg",
          variantQty: 10
        },
        {
          variantId: 3335,
          variantColor: "#233349",
          variantImg: "../assets/scocks-2.jpeg",
          variantQty: 0
        }
      ]
    };
  },
  methods: {
    addToCart() {
      this.$emit("add-to-cart", this.variants.variantId);
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
    },
    inStock() {
      return this.variants[this.selectedVariant].variantQty;
    },
    shipping() {
      if (this.premium) {
        return "Free";
      } else {
        return "$" + 1.99;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.product {
  margin-top: 30px;
  display: flex;
  align-items: flex-start;
  justify-content: space-evenly;
}

h5 {
  color: #45aa7b;
  margin-bottom: 5px;
  margin-top: 15px;
}

.bold {
  color: rgb(26, 46, 39);
}

.desc {
  margin-bottom: 25px;
}

ul {
  margin-bottom: 20px;
}

button {
  margin-top: 35px;
  display: block;
  appearance: none;
  border: 0;
  border-radius: 5px;
  font-size: 16px;
  padding: 10px 20px;
  color: #fff;
  font-weight: 400;
  background-color: #45aa7b;
  cursor: pointer;
}

.disabledButton {
  background-color: lightgrey;
}

img {
  width: 350px;
}

.color-option {
  display: flex;
  margin-bottom: 5px;
}

.color-box {
  width: 50px;
  height: 50px;
}
</style>
