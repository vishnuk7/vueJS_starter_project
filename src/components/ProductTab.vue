<template>
  <div>
    <div class="tabs">
      <span
        :class="{activeTab: selectedTab === tab}"
        v-for="(tab,index) in tabs"
        :key="index"
        @click="selectedTab = tab"
      >{{tab}}</span>
    </div>

    <div v-show="selectedTab === 'Reviews'" class="product-review">
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
          <p>
            <span class="review-tag">Recommending :</span>
            <span class="rating">{{ review.recommend }}</span>
          </p>
        </li>
      </ul>
    </div>

    <ProductReview v-show="selectedTab === 'Make a Review' " @review-submitted="addReview" />
  </div>
</template>

<script>
import ProductReview from "./ProductReview";
export default {
  name: "ProductTab",
  components: {
    ProductReview
  },
  props: {
    reviews: {
      type: Array,
      required: false
    }
  },
  data() {
    return {
      tabs: ["Reviews", "Make a Review"],
      selectedTab: "Reviews"
    };
  },
  methods: {
    addReview(productReview) {
      this.reviews.push(productReview);
    }
  }
};
</script>

<style scoped>
li {
  list-style: none;
}

.tabs {
  display: flex;
  justify-content: center;
  margin-bottom: 15px;
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
</style>