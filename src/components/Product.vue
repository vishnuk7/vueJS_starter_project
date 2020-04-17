<template>
  <div>
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
          <span class="shipping-tag">shipping</span>
        </small>
        <small v-else>Out of Stock</small>

        <button
          @click="addToCart"
          :disabled="!inStock"
          :class="{ disabledButton: !inStock }"
        >Add to Cart</button>
      </div>
    </div>
    <div class="product-review">
      <h5>Review</h5>
      <p v-if="!reviews.length" style="color:#868686">There are no reviews yet.</p>
      <ul>
        <li v-for="(review,index) in reviews" :key="index">
          <p>
            <span class="review-tag">Name:</span>
            <span>{{ review.name }}</span>
          </p>
          <p>
            <span class="review-tag">Review:</span>
            <span>{{ review.review }}</span>
          </p>
          <p>
            <span class="review-tag">Rating:</span>
            <span class="rating">{{ review.rating }}</span>
          </p>
        </li>
      </ul>
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
    },
    reviews: {
      type: Array
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
  color: rgb(35, 51, 73);
  margin: 0 5px;
  font-size: 31px;
}

.desc {
  margin-bottom: 25px;
}

ul {
  margin-bottom: 20px;
}

li {
  list-style: none;
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

.product-review {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.product-review ul {
  width: 80%;
}

.product-review li {
  margin-bottom: 12px;
  border: 1px solid #d7d7d7;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 2px 3px 5px #b5b5b5;
}

.product-review p {
  margin-bottom: 9px;
}

.review-tag {
  color: #333;
  margin-right: 5px;
}

.rating {
  color: #45aa7b;
  font-weight: bold;
}

.shipping-tag {
  background-color: #45aa7b;
  color: #fff;
  font-weight: bold;
  padding: 5px;
  font-size: 10px;
  border-radius: 10px;
}

small {
  display: flex;
  align-items: center;
}
</style>
