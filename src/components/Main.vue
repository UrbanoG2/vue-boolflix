<template>
    <div class="big-container">
        <h1 v-if="Movies.length > 0" >Film</h1>
        <div v-if="Movies.length > 0" class="films">
            <div class="movie" v-for="(movie,index) in Movies"
                :key="index+movie.id">
                <div class="img-container">
                    <img :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path" :alt="movie.title">

                </div>
                <div class="thumb-text">
                    <h2>{{ movie.title }}</h2>
                    <h3>{{ movie.original_title }}</h3>
                    <!-- richiamo la bandiera tramite la funzione che ho creato -->
                    <i :class="'flag flag-' + getFlag(movie.original_language)"/>
                    
                    <h4>{{ movie.vote_average }}</h4>
                </div>
            </div>
        </div>
        <div v-else > Non ci sono film che soddisfino i criteri di ricerca</div>

        <h1 v-if="Series.length > 0" >Tv Series</h1>
        <div v-if="Series.length > 0" class="series">
            <div class="serie" v-for="(serie,index) in Series"
                :key="index+serie.id">
                <img :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path" :alt="serie.name">
                <div class="thumb-text">
                    <h2>{{ serie.name }}</h2>
                    <h3>{{ serie.original_name }}</h3>
                    <i :class="'flag flag-' + getFlag(serie.original_language)"/>
                    <h4>{{ serie.vote_average }}</h4>
                </div>
            </div>
        </div>
        <div v-else > Non ci sono serie che soddisfino i criteri di ricerca</div>
    </div>
</template>

<script>


export default {

    nome:"Main",
    props: 
        ["Movies","Series","image"],

    data() {
        return {
            intNumber:"",
        }
    },

    methods: {

        //associamo la bandiera degli USA alla lingua "en", perchè non esiste una bandiera en :)
        getFlag(language) {
            switch (language){
                case "en": 
                    return "us";
                default:     
                    return language
            }
        },
    }
}
</script>

<style lang="scss" scoped>
    @import '~mdb-ui-kit/css/mdb.min.css';
   .big-container {
       width: 80%;
       margin: 0 auto;
       .films,
       .series {
           display: flex;
           flex-wrap: wrap;
           justify-content: center;
           
       }
       .movie,
       .serie {
           display: flex;
           flex-direction: column;
           flex-wrap: wrap;
           border: 1px solid white;
           padding: 1em;
           margin: 10px;


           .thumb-text {
               width: 342px;
               color: white;
               text-align: center;
               
               h2,
               h3,
               h4 {
                   margin-top: 10px;
                   font-size: 1.2em;
               }
           }
       }
       h1 {
           text-align: center;
            color: white;
       }
   }
</style>