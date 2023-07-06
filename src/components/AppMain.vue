<!---------------- Script ----------------->

<script>

// Import
import SearchInput from './SearchInput.vue';
import axios from 'axios';
import AppCard from './AppCard.vue';
import { store } from '../data/store';
import { api } from '../data/index';



export default {
    components: {SearchInput , AppCard},
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
            <AppCard v-for="movie in store.movies" :key="movie.id" :item="movie"/>
        </ul>

        <h2> Series</h2>
        <ul>
            <AppCard v-for="serie in store.series" :key="serie.id" :item="serie"/>
        </ul>

    </main>

</template>







<!---------------Style -------------->

<style scoped>



</style>
