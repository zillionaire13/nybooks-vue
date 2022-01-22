<template>
  <div class="topsellers">
    
  </div>
</template>

<script>

export default {
  name: "Topsellers",
  data(){
    return {
      url: `https://api.nytimes.com/svc/books/v3/lists/overview.json?api-key=${process.env.VUE_APP_API}`,
      lists : [],
    }
  },
  methods: {
    async fetchFromAPI() {
      let res = await fetch(this.url)
      let data = res.json()
      return data
    },

  },
  async mounted() {
    if(!localStorage.getItem('fetchedData')){
      let predata = await this.fetchFromAPI()
      localStorage.setItem('fetchedData', JSON.stringify(predata))
    }
    this.lists = JSON.parse(localStorage.getItem('fetchedData')).results.lists
  }
}
</script>

