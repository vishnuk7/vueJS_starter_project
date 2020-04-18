<template>
  <div>
    <div class="make-center">
      <div class="review-error" v-if="errors.length">
        <b>Please correct the following error(s) :</b>
        <ul>
          <li v-for="(error,index) in errors" :key="index">* {{ error }}</li>
        </ul>
      </div>
    </div>

    <form @submit.prevent="onSubmit">
      <div class="form">
        <label for="name">Name</label>
        <input v-model="name" id="name" type="text" autofocus placeholder="Enter your name" />
      </div>

      <div class="form">
        <label for="review">Review</label>
        <textarea
          v-model="review"
          id="review"
          type="text"
          placeholder="Enter your review"
          rows="4"
          cols="50"
        ></textarea>
      </div>

      <div class="form">
        <label for="rating">Rating</label>
        <select id="rating" v-model.number="rating">
          <option value="5" selected>5</option>
          <option>4</option>
          <option>3</option>
          <option>2</option>
          <option>1</option>
        </select>
      </div>

      <div class="form">
        <label for="recommend">Would you recommend this product</label>
        <input type="radio" name="recommend" id="recommend" value="yes" />Yes
        <input type="radio" name="recommend" id="recommend" value="no" />No
      </div>

      <div class="form-btn">
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "ProductReview",
  data() {
    return {
      name: null,
      review: null,
      rating: null,
      errors: []
    };
  },
  methods: {
    onSubmit() {
      if (this.name && this.review && this.rating) {
        let productReview = {
          name: this.name,
          review: this.review,
          rating: this.rating
        };
        this.$emit("review-submitted", productReview);

        this.name = null;
        this.review = null;
        this.rating = null;
      } else {
        if (!this.name) this.errors.push("Name required");
        if (!this.review) this.errors.push("Review required");
        if (!this.rating) this.errors.push("Rating required");
      }
    }
  }
};
</script>

<style lang="css" scoped>
form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 60vw;
  margin-bottom: 10px;
}

input[type="text"],
textarea {
  appearance: none;
  outline: none;
  border-radius: 5px;
  padding: 5px 10px;
  border: 1px solid #ccc;
  width: 80%;
  display: flex;
  color: #222;
  font-size: 17px;
}
input[type="text"]::placeholder,
textarea::placeholder {
  color: #333;
}

input[type="radio"] {
  appearance: none;
  border: 1px solid #d5d5d5;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  transition: all 0.2s;
  cursor: pointer;
}

input[type="radio"]:hover {
  background: #aeaeae;
}

input[type="radio"]:checked {
  background: #45aa7b;
  padding: 2px;
}
select {
  appearance: none;
  outline: none;
  border-radius: 5px;
  padding: 5px 10px;
  border: 1px solid #ccc;
  width: 80%;
  display: flex;
  background: #fff;
}
button {
  appearance: none;
  background-color: #45aa7b;
  color: #fff;
  padding: 5px 20px;
  font-weight: bold;
  border: 0;
  border-radius: 5px;
}

.review-error {
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 15px;
  background: #ffefef;
  width: 80vw;
  border-radius: 10px;
}

b {
  font-size: 13px;
  margin-bottom: 4px;
  color: #ff4757;
}

.review-error li {
  list-style: none;
  color: #ff4757;
  font-size: 12px;
  font-weight: 600;
  margin-bottom: 5px;
}

.make-center {
  display: flex;
  justify-content: center;
}
</style>