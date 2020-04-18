<template>
  <div class="tabs">
    <span
      :class="{activeTab: selectedTab === tab}"
      v-for="(tab,index) in tabs"
      :key="index"
      @click="selectedTab = tab"
    >{{tab}}</span>
  </div>
</template>

<script>
export default {
  name: "ProductTab",
  data() {
    return {
      tabs: ["Reviews", "Make a Review"],
      selectedTab: "Review"
    };
  }
};
</script>

<style scoped>
.tabs {
  display: flex;
  justify-content: center;
}
.tabs span {
  margin-right: 20px;
  cursor: pointer;
}

.activeTab {
  color: #45aa7b;
  border-color: #45aa7b;
  border-bottom: 2px solid;
  padding-bottom: 5px;
  transition: all 0.5s;
}
</style>