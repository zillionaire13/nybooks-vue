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
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 1rem;
  padding: 10px;
}

.cards {
  /* border: 1px solid black; */
  border-radius: 6px;
  padding: 10px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}

.card {
  display: flex;
  flex-flow: column;
  justify-content: space-between;
  position: relative;
  padding-top: 25px;
}

.book-title {
  font-size: 1rem;
  font-weight: semibold;
}

.author {
  font-size: 1rem;
}

.description {
  font-size: 1rem;
  text-align: left;
  padding: 1rem;
}

.button-link > a {
  text-decoration: none;
  color: inherit;
}

.button-link {
  cursor: pointer;
}

.button {
  display: block;
  padding: 10px;
  background-color: lightblue;
  border-radius: 6px;
  border: none;
  margin: 0 auto;
}

.button-link:hover {
  background-color: rgb(16, 121, 240);
  color: white;
}

.image > img {
  object-fit: contain;
  max-height: 50vh;
  min-height: 50vh;
}

.book-rank{
  position: absolute;
  top: -26px;
  right: 0;
  background-color: orangered;
  padding: 10px;
  border-radius: 0 0px 6px 6px;
  color: white;
}
</style>
