<template>
  <div id="app">
    <Header @doSearch="search($event)">
      <!-- prendo l'array che ho creato nell'header, gli do un valore con una funzione (qui sotto) e poi lo richiamo con le props nel main-->
    </Header> 
    

    <Main :Movies="Filtered.selectedMovies"
          :Series="Filtered.selectedSeries">
          
      <!-- questa è la props che ho nel main -->
    </Main>
    
  </div>
</template>

<script>

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";


export default {
  name: "App",
  components: {
    Header,
    Main
  },

  data (){
    return {

      Filtered: {
         selectedMovies:[],
         selectedSeries:[],
      }
     
    }
  },

  methods: {
      search(value) { 
        this.Filtered.selectedMovies = value.movies; 
        this.Filtered.selectedSeries = value.series;
      }
  },
  
};
</script>

<style lang="scss">

</style>
