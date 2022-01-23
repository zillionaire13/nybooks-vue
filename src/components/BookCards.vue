<template>
  <v-container grid-list-xs>
    <v-row >
      <v-col v-for="(book, i) in value.books" :key="i" cols="4" class="d-flex align-stretch">
          <v-card class="pa-5 d-flex justify-around flex-column" elevation="1"> 
            <h1 class="text-h5 font-weight-bold ">{{book.title}}</h1>
            <p class="book-rank"> #{{ book.rank }}</p>
            <v-img :src="book.book_image"></v-img>
            <v-row>
              <v-col>
                <p class="author">{{ book.author }}</p>
                <p class="description">{{ book.description }}</p>
                <code class="isbn13">ISBN: {{ book.primary_isbn13 }}</code>
              </v-col>
            </v-row>
            <v-btn
              color="primary"
              depressed
              elevation="2"
              large
            >Buy from Amazon</v-btn>
          </v-card>
      </v-col>
    </v-row>
  </v-container>
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
