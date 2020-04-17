<template>
  <div class="product">
    <div class="product-image">
      <img :src="img" :alt="product" />
    </div>
    <div class="product-info">
      <h5>{{ product }}</h5>
      <p>{{ description }}</p>
      <p v-if="isStock">In Stock</p>
      <p v-else>Out of Stock</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Product",
  data() {
    this.product = "Scoks";
    this.description = "A pair of warm, fuzzy socks";
    this.img = "../assets/scoks-1.jpeg";
    this.isStock = false;
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  width: 450px;
}
</style>
