<template>
    <div>
        <input type="text" placeholder="Cerca il tuo film"
                v-model="searchText"
                 >
        <button @click="completeApi">Cerca</button>
        <!-- input sopra con v-model e click sotto, niente di complicato -->

    </div>
</template>

<script>

import axios from "axios";

export default {
    nome:"Header",
    data () {
        return {  //data per creare lAPI completa
            searchText: "",
            apiStatic:"https://api.themoviedb.org/3/search/movie?api_key=6e3e98384f214afec2e321508faaee73&query=",
            apiDynamic:"",
            movies:[]
        }
    },

    methods: {  //faccio tutto in un metodo: creo la mia API completa sommando i miei data e successivamente creo la chiamata AXIOS 
       completeApi() {
           this.apiDynamic = this.apiStatic + this.searchText;
           console.log(this.apiDynamic);

            axios
                .get (this.apiDynamic)
                .then((response)=>{
                this.movies = response.data.results;

                //sparo direttamente l'array dall'altra parte
                this.$emit("doSearch", this.movies);
                console.log(this.movies);

                }).catch ((error)=>{
                    console.log(error);
                })

                this.searchText=""
       } 
  },


}
</script>

<style lang="scss" scoped>

</style>