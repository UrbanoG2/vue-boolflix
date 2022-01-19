<template>
    <div>
        <input type="text" placeholder="Cerca il tuo film"
                v-model="searchText"
                 >
        <button @click="$emit('search', searchText)">Cerca</button>

        <!-- @click="$emit('search', searchText)" -->
    </div>
</template>

<script>
export default {
    nome:"Header",
    props: {
        inputValue:String,
    },
    data () {
        return {
            searchText: "",
        }
    },


    // created () {
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