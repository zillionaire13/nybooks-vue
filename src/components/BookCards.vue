<template>
  <div>
    <div class="container">
      <div class="cards" v-for="(book, i) in value.books" :key="i">
        <div class="card">
          <h1 class="book-title">{{ book.title }}</h1>
          <p class="book-rank"> #{{ book.rank }}</p> 
          <div class="image">
            <img :src="book.book_image" alt="Book Image" />
          </div>
          <div class="card-body">
            <p class="author">{{ book.author }}</p>
            <p class="description">{{ book.description }}</p>
            <p class="isbn13">{{ book.isbn13 }}</p>
          </div>
          <button class="button button-link">
            <a :href="book.amazon_product_url">Buy on Amazon</a>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BookCards",
  props: ["value"],
  data() {
    return {};
  },
  mounted() {
    console.log(this.value);
  },
};
</script>

<style scoped>

</style>
