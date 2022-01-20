<template>
    <div>
        <input  @keyup.enter="getBoth" type="text" placeholder="Cerca il tuo film"
                v-model="searchText"
                 >
        <button @click="getBoth">Cerca</button>
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
            apiStaticMovies:"https://api.themoviedb.org/3/search/movie?api_key=6e3e98384f214afec2e321508faaee73&query=",
            apipStaticSeries:"https://api.themoviedb.org/3/search/tv?api_key=6e3e98384f214afec2e321508faaee73&language=it_IT&query=",
            apiMovies:"",
            apiSeries:"",
            // movies:[],
            // series:[],
            finalArr: {
                movies:[],
                series:[]
            }
        }
    },

    methods: {  //faccio tutto in un metodo: creo la mia API completa sommando i miei data e successivamente creo la chiamata AXIOS 
       

        // getMerged() {
        //    let mergedArr = [...this.movies, ...this.series]
        //    console.log(mergedArr);  
        // },



        getBoth() {
            this.getMovies(),
            this.getSeries(),
            setTimeout(() => {
                this.$emit("doSearch", this.finalArr);
            }, 500);
            
        },
        
        getMovies() {
           this.apiMovies = this.apiStaticMovies + this.searchText;
           console.log(this.apiMovies);

            axios
                .get (this.apiMovies)
                .then((response)=>{
                this.finalArr.movies = response.data.results;

                console.log(this.finalArr.movies);

                }).catch ((error)=>{
                    console.log(error);
                })

        },


        
        
        getSeries() {
           this.apiSeries = this.apipStaticSeries + this.searchText;
           console.log(this.apiSeries);

            axios
                .get (this.apiSeries)
                .then((response)=>{
                this.finalArr.series = response.data.results;

                console.log(this.finalArr.series);

                }).catch ((error)=>{
                    console.log(error);
                })
        } ,


       
  },


}
</script>

<style lang="scss" scoped>

</style>