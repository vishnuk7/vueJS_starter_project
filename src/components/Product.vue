<template>
  <div>
    <h5>{{ product }}</h5>
    <p>{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: "Product",
  data() {
    this.product = "Scoks";
    this.description = "A pair of warm, fuzzy socks";
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
