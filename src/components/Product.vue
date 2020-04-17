<template>
  <div class="product">
    <div class="product-image">
      <img :src="img" :alt="product" />
    </div>
    <div class="product-info">
      <h5>{{ product }}</h5>
      <p>{{ description }}</p>
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
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
