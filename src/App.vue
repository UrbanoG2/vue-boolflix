<template>
  <div id="app">
    <Header @doSearch="search($event)">
      <!-- ricevo dall'header (dove ho fatto l'emit) l'oggetto contenente i due array. L'event lo richiamo nella funzione search che ho qui sotto-->
    </Header> 
    
    <!-- definisco i due elementi del main, prendendo le props dal main stesso, e le associo al valore che ho nei data -->
    <Main :Movies="Filtered.selectedMovies"
          :Series="Filtered.selectedSeries">
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
      //data in cui inserisco i valori, in questo caso inserisco un oggetto che ha al suo interno i due array vuoti
      Filtered: {
         selectedMovies:[],
         selectedSeries:[],
      }
     
    }
  },

  methods: {

    //funzione che parte da dove ho ricevuto l'emit, nella qualche dico che i miei data sono uguali al valore che gli ho passato sopra (nel mio caso il valore è finalArr, che è un oggetto, specifico poi cosa voglio di quell'oggetto)
      search(value) { 
        this.Filtered.selectedMovies = value.movies;
        this.Filtered.selectedSeries = value.series;
      }
  },
  
};
</script>

<style lang="scss">
  #app {
    // height: 100vh;
    background-color: RGB(20, 20, 20);
  }

  @import "./assets/scss/style.scss"
</style>  
