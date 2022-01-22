<template>
  <div class="topsellers">
    <h3>Top 5 Books from The BestSellers by Category</h3>
    <div>
      <select 
        @change="changeCategory"
        name="seller-select" 
        id="seller-select"
      >
        <option :value="list.list_id" v-for="(list, i) in lists" :key="i"> {{list.display_name}} </option>
      </select>
    </div>
      <h1 class="category-title"> {{ listItem.display_name }} </h1>
      <book-cards-vue :value="listItem"></book-cards-vue>
  </div>
</template>

<script>

import BookCardsVue from "@/components/BookCards.vue"

export default {
  name: "Topsellers",
  components: {
    BookCardsVue
  },
  data() {
    return {
      url: `https://api.nytimes.com/svc/books/v3/lists/overview.json?api-key=${process.env.VUE_APP_API}`,
      lists: [],
      listItem: ''
    };
  },
  methods: {
    async fetchFromAPI() {
      let res = await fetch(this.url);
      let data = res.json();
      return data;
    },
    changeCategory(e){
      this.listItem = this.lists.find(el => e.target.value == el.list_id)
    }
  },
  async mounted() {
    if (!localStorage.getItem("TopSellersData")) {
      let predata = await this.fetchFromAPI();
      localStorage.setItem("TopSellersData", JSON.stringify(predata));
    }
    this.lists = JSON.parse(localStorage.getItem("TopSellersData")).results.lists;
    this.listItem = this.lists[0]
  },
};
</script>

<style scoped>
.category-title {
  font-size: 1.2rem;
}

#seller-select{
  padding: 15px;
}
</style>

