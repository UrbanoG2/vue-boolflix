<template>
  <div id="app">
    <Header @doSearch="search($event)">
      <!-- prendo l'array che ho creato nell'header, gli do un valore con una funzione (qui sotto) e poi lo richiamo con le props nel main-->
    </Header> 
    

    <Main :Movies="selectedMovies">
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
      selectedMovies:"" 
    }
  },

  methods: {
      search(value) { 
        this.selectedMovies = value; //funzione dell'emit
      }
  },
  
};
</script>

<style lang="scss">

</style>
