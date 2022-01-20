<template>
    <div>
        <ul v-for="(movie,index) in Movies"
            :key="index">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul>

        <ul v-for="(serie,index) in Series"
            :key="index+'16'" >
            <li>{{ serie.name }}</li>
            <li>{{ serie.original_name }}</li>
            <li>{{ serie.original_language }}</li>
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
}
</script>

<style lang="scss" scoped>

</style>