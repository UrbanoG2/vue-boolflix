<template>
    <div class="header">
        <img src="../assets/img/bool-logo.png" alt="">

        <div class="search-container">
            <input  @keyup.enter="getBoth" type="text" placeholder="Cerca il tuo film"
                v-model="searchText"
                 >
            <!-- <button @click="getBoth">Cerca</button> -->
        </div>
        <!-- input sopra con v-model e click sotto, niente di complicato -->
    </div>
</template>

<script>

import axios from "axios";

export default {
    nome:"Header",
    data () {
        return {  //data per creare l'API completa
            searchText: "",
            apiStaticMovies:"https://api.themoviedb.org/3/search/movie?api_key=6e3e98384f214afec2e321508faaee73&query=",
            apipStaticSeries:"https://api.themoviedb.org/3/search/tv?api_key=6e3e98384f214afec2e321508faaee73&language=it_IT&query=",
            apiMovies:"",
            apiSeries:"",
            //oggetto contenente i due array
            finalArr: {
                movies:[],
                series:[]
            }
        }
    },

    methods: {  //faccio tutto in un metodo: creo la mia API completa sommando i miei data e successivamente creo la chiamata AXIOS 
    

    //questa è la funzione che richiamo al click, chiamo entrambe le funzioni che mi servono (con un timeout per farle funzionare)
        getBoth() {
            this.getMovies(),
            this.getSeries(),
            setTimeout(() => {

                //qui faccio l'emit, con il quale passo il dato che voglio (in questo caso l'oggetto che contiene i due array. Passo l'intero oggetto così da gestire i suoi elementi)
                this.$emit("doSearch", this.finalArr);
            }, 500);
            
        },
        
        getMovies() {
           this.apiMovies = this.apiStaticMovies + this.searchText;
           console.log(this.apiMovies);
            //all'interno di entrambe le mie funzioni costruisco l'api completa e poi faccio la chiamata AXIOS sulla predetta api
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
            //stessa cosa di sopra
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
    .header {
        background-color: black;
        display: flex;
        align-items: center;
        justify-content: space-between;
        img {
            width: 10%;
            padding: 2em 0;
            margin: 0 1em;
           
        }

        .search-container {
            margin-right: 2em;

            input {
                margin-right:2em;
                color: white;
                background-color: black;
                border: none;
            }
        }

    }
</style>