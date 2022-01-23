<template>
  <v-container grid-list-xs>
    <v-row v-if="loading" class="d-inline text-center">
        <h1>Loading....</h1>
      </v-row>
    <v-row v-else>
      <v-col>
        <v-select
          @change="changeCategory"
          name="seller-select"
          outline
          dense
          label="Select Category"
          :items="selectOptions"
        ></v-select>
      </v-col>
      <v-row>
        <book-cards-vue :value="listItem">
        </book-cards-vue>
      </v-row>
    </v-row>
  </v-container>
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
      listItem: '',
      loading: true
    };
  },
  methods: {
    async fetchFromAPI() {
      let res = await fetch(this.url);
      let data = res.json();
      return data;
    },
    changeCategory(e) {
      this.listItem = this.lists.find(el => e == el.list_id)
    }
  },
  async mounted() {
    if (!localStorage.getItem("TopSellersData")) {
      let predata = await this.fetchFromAPI();
      localStorage.setItem("TopSellersData", JSON.stringify(predata));
    }
    this.lists = JSON.parse(localStorage.getItem("TopSellersData")).results.lists;
    this.listItem = this.lists[0]
    this.loading = false
  },
  computed: {
    selectOptions(){
      let data = this.lists.map((x) => ({text: x.display_name, value: x.list_id})  )
      return data
    }
  }
};
</script>

<style scoped>
</style>

  
