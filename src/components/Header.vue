<template>
    <div>
        <input type="text" placeholder="Cerca il tuo film"
                v-model="searchText"
                 >
        <button @click="completeQuery" >Cerca</button>
    </div>
</template>

<script>
export default {
    nome:"Header",
    data () {
        return {
            searchText: "",
            queryStatic:"https://api.themoviedb.org/3/search/movie?api_key=6e3e98384f214afec2e321508faaee73&query=",
            queryDynamic:"",
        }
    },

    methods: {
        completeQuery() {
            this.queryDynamic = this.queryStatic + this.searchText;
            console.log(this.queryDynamic);
            this.searchText=""
        } 
    },

    // mounted () {
    //     axios
    //         .get (this.queryDynamic)
    //         .then((response)=>{
    //             console.log(response);

    //         }).catch ((error)=>{
    //             console.log(error);
    //     })
    // },

}
</script>

<style lang="scss" scoped>

</style>