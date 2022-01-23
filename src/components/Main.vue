<template>
    <div class="big-container">
        <h1 v-if="Movies.length > 0" >Film</h1>
        <div v-if="Movies.length > 0" class="films">
            <div class="movie" v-for="(movie,index) in Movies"
                :key="index+movie.id">
                <div class="img-container">
                    <img
                    v-if="movie.poster_path" 
                    :src="`https://image.tmdb.org/t/p/w342${movie.poster_path}`" :alt="movie.title">

                    <img class="stock-image"
                    v-else
                    src="https://img3.stockfresh.com/files/a/andreypopov/m/98/3838831_stock-photo-movie-production-clapper-board-on-white-background.jpg" alt="Nessuna immagine trovata">
                </div>

                <div class="active-hover">
                    <div class="thumb-text">
                        <h2>{{ movie.title }}</h2>
                        <h3>{{ movie.original_title }}</h3>
                        <!-- richiamo la bandiera tramite la funzione che ho creato -->
                        <i :class="'flag flag-' + getFlag(movie.original_language)"/>
                        VOTO: {{ getNewVote(movie.vote_average) }} <i v-for="(number, index) in 5"
                        :key="number"
                        :class="(index <=  getNewVote(movie.vote_average) ? 'fas fa-star' : 'far fa-star')"></i>
                        
                        <p>
                            {{ movie.overview }}
                        </p>
                        <!-- <h4>{{ getNewVote(movie.vote_average) }}</h4> -->
                    </div>
                </div>
                
            </div>
        </div>
        <div v-else > Non ci sono film che soddisfino i criteri di ricerca</div>

        <h1 v-if="Series.length > 0" >Tv Series</h1>
        <div v-if="Series.length > 0" class="series">
                <div class="serie" v-for="(serie,index) in Series"
                    :key="index+serie.id">
                    <div class="img-container">
                        <img
                        v-if="serie.poster_path" 
                        :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" :alt="serie.title">

                        <img class="stock-image"
                        v-else
                        src="https://img3.stockfresh.com/files/a/andreypopov/m/98/3838831_stock-photo-serie-production-clapper-board-on-white-background.jpg" alt="Nessuna immagine trovata">
                    </div>

                    <div class="active-hover">
                        <div class="thumb-text">
                            <h2>{{ serie.title }}</h2>
                            <h3>{{ serie.original_title }}</h3>
                            <!-- richiamo la bandiera tramite la funzione che ho creato -->
                            <i :class="'flag flag-' + getFlag(serie.original_language)"/>
                            VOTO: {{ getNewVote(serie.vote_average) }} <i v-for="(number, index) in 5"
                            :key="number"
                            :class="(index <=  getNewVote(serie.vote_average) ? 'fas fa-star' : 'far fa-star')"></i>
                            
                            <p>
                                {{ serie.overview }}
                            </p>
                            <!-- <h4>{{ getNewVote(serie.vote_average) }}</h4> -->
                        </div>
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
            
        }
    },

    methods: {

        //associamo la bandiera degli USA alla lingua "en", perchè non esiste una bandiera en :)
        //switch case per poi capire se ci sono più situazioni simili
        getFlag(language) {
            switch (language){
                case "en": 
                    return "us";
                default:     
                    return language
            }
        },

        getNewVote (vote) {
           return Math.round(vote / 2)
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '~mdb-ui-kit/css/mdb.min.css';

    .big-container {
       width: 80%;
       margin: 0 auto;
       background-color: RGB(20, 20, 20);

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
           padding: 0.5em;
           margin: 10px;
           .img-container {
                img.stock-image {
                   width: 342px;
                }
           }


        
            .active-hover {
                display: none;
                position: absolute;
                background-color: RGB(20, 20, 20);
                opacity: 0.9;
                height: 513px;
                width: 342px;
                cursor: pointer;
           


                .thumb-text {
                    width: 342px;
                    color: white;
                    text-align: center;
                    overflow-y: auto;
                    height: 100%;

                    
                    
                    h2,
                    h3,
                    h4 {
                        margin-top: 10%;
                        font-size: 1.2em;

                    }

                    p {
                        margin-top: 15%;
                    }
                }
        
            }
        }

         h1 {
            text-align: center;
                color: white;
        
            }

        .movie:hover .active-hover,
        .serie:hover .active-hover {
             display: block;
        }

        ::-webkit-scrollbar {
            width: 7px;
        }

        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }

        ::-webkit-scrollbar-thumb {
            background: rgb(194, 194, 194);
        }
    }
</style>