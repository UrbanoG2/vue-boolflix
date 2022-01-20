<template>
    <div>
        <ul v-for="(movie,index) in Movies"
            :key="index">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li><i :class="'flag flag-' + getFlag(movie.original_language)" /></li>
            <li>{{ movie.vote_average }}</li>

            <!-- <li>`<i class="flag flag-${movie.original_language}"></i>`</li> -->
        </ul>

        <ul v-for="(serie,index) in Series"
            :key="index+'16'" >
            <li>{{ serie.name }}</li>
            <li>{{ serie.original_name }}</li>
            <li><i class="flag flag-united-states"></i></li>
            <li>{{ serie.vote_average }}</li>
        </ul>
    </div>
</template>

<script>


export default {

    nome:"Main",
    props: 
        ["Movies","Series"],

    data() {
        return {

        }
    },

    methods: {

        //associamo la bandiera degli USA alla lingua "en", perchè non esiste una bandiera en :)
        getFlag(language) {
            if (language == "en") {
                return "us"
            } return language
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '~mdb-ui-kit/css/mdb.min.css';

</style>