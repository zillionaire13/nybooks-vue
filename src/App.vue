<template>
  <v-app>
    <v-container grid-list-xs>
      <v-row>
        <v-col>
          <v-tabs class="d-flex justify-center">
            <v-tab to="/">Home</v-tab>
            <v-tab to="/topsellers">TopSellers</v-tab>
          </v-tabs>  
        </v-col>  
      </v-row>          
    </v-container>
    <router-view/>
  </v-app>
</template>


