<template>
    <div>
        <ul v-for="(movie,index) in movies"
            :key="index">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>voto</li>

        </ul>
    </div>
</template>

<script>

import axios from "axios";

export default {


    nome:"Main",
    props: {
        completeApi:String,
    },
    data() {
        return {
            movies: [],
        }
    },

    mounted () {
        axios
        .get (this.completeApi)
        .then((response)=>{
            this.movies = response.data.results;
            // console.log(response.data.results)
            console.log(this.movies);

        }).catch ((error)=>{
            console.log(error);
        })
    },

}
</script>

<style lang="scss" scoped>

</style>