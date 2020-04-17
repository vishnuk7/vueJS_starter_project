<template>
  <div>
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
      rating: null
    };
  },
  methods: {
    onSubmit() {
      let productReview = {
        name: this.name,
        review: this.review,
        rating: this.rating
      };
      this.$emit("review-submitted", productReview);

      this.name = null;
      this.review = null;
      this.rating = null;
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
</style>