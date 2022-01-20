<template>
    <div>
        <ul v-for="(movie,index) in Movies"
            :key="index">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>

        </ul>
    </div>
</template>

<script>

export default {


    nome:"Main",
    props: 
        ["Movies"],
    
    data() {
        return {
        }
    },
}
</script>

<style lang="scss" scoped>

</style>