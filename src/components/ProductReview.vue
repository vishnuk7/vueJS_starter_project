<template>
  <div>
    <form>
      <input v-model="name" type="text" autofocus placeholder="Enter your name" />
    </form>
  </div>
</template>

<script>
export default {
  name: "ProductReview",
  data() {
    return {
      name: null
    };
  }
};
</script>

<style lang="css" scoped>
</style>