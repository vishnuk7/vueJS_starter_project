<template>
  <div class="header">
    <div class="brand">
      <h2>
        <span class="s">S</span>
        <span>hop</span>
        <span class="o">O</span>
        <span class="shopo">!</span>
      </h2>
    </div>
    <div class="user">
      <p v-if="premium">Premium User</p>
      <p v-else>Become a premium user</p>
      <div class="cart">{{ cart }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: ["cart", "premium"]
};
</script>

<style scoped>
.s {
  color: #45aa7b;
}

.shopo {
  background: #45aa7b;
  color: #fff;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 8px 0;
}

.user {
  display: flex;
  justify-content: center;
  align-items: center;
}

.cart {
  background-color: #45aa7b;
  color: #fff;
  font-weight: bold;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.header p {
  margin-right: 10px;
  color: darkslategrey;
  font-size: 14px;
  font-weight: bold;
}
</style>