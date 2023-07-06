<!---------------- Script ----------------->

<script>

// Import
import SearchInput from './SearchInput.vue';
import axios from 'axios';
import { store } from '../data/store';
import { api } from '../data/index';



export default {
    components: {SearchInput},
    data() {
        return {
            store,
            titleFilter: '',
        }
    },

    methods: {
        
        setTitleFilter(term) {
            this.titleFilter = term
        },

        searchProduction() {
            if(!this.titleFilter) {
                store.movies = [];
                store.series = []
                return;
            }

            this.fetchProduction('search/movie', 'movies')
            this.fetchProduction('search/tv', 'series')
        },

        fetchProduction(endpoint, target) {
            axios.get(`${api.baseUri}/${endpoint}?api_key=${api.key}&query=${this.titleFilter}&language=${api.language}`).then( res => {
            store[target] = res.data.results;
            })
        },
    }
}


</script>








<!--------------- Template ------------->

<template>
  
    <!--- SearchInput ---->
    <SearchInput @term-change="setTitleFilter" @form-submit="searchProduction"/>



    <!----- Main ------->
    <main>
        <h2> Movies</h2>
        <ul>
            <li v-for="movie in store.movies" :key="movie.id"> {{ movie.original_title }}</li>
        </ul>

        <h2> Series</h2>
        <ul>
            <li v-for="serie in store.series" :key="serie.id"> {{ serie.original_name }}</li>
        </ul>

    </main>

</template>







<!---------------Style -------------->

<style scoped>



</style>
