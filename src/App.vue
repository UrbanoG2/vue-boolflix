<template>
  <div id="app">
    <Header @search="completeApi($event)" >
      
      </Header> 
    
    <!-- :inputValue="apiDynamic -->

    <Main :completeApi="apiDynamic">

      
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
      apiStatic:"https://api.themoviedb.org/3/search/movie?api_key=6e3e98384f214afec2e321508faaee73&query=",
      apiDynamic:"",
    }
  },

  methods: {
       completeApi(value) {
           this.apiDynamic = this.apiStatic + value;
           console.log(this.apiDynamic);
           this.searchText=""
       } 
  },

  
};
</script>

<style lang="scss">

</style>
