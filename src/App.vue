<!---------------- Script ----------------->

<script>

// Import
import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';
import axios from 'axios';
import { store } from './data/store';

const endpoint = 'https://api.themoviedb.org/3/search/movie?api_key=9d8ac34de279b31f93bfd5a7c1db6ad2&query=anelli&language=it-IT'


export default {
    components: {AppMain , AppHeader},
    data() {
        return {
            
        }
    },
    created() {
        axios.get(endpoint).then( res => {
            store.movies = res.data.results;
        })
    }
} 

</script>








<!--------------- Template ------------->

<template>
  

    <!------ AppHeader ------->
    <AppHeader />



    <!----- AppMain ------>
    <AppMain />


</template>







<!---------------Style -------------->

<style lang="scss">

@use './assets/scss/style.scss';

</style>
