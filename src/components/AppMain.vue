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
    
    <div class="container">

        <div class="social">
            <img src="../assets/img/pngwing.com.png" alt="Beholder">
            <i class="fa-brands fa-square-facebook"></i>
            <i class="fa-brands fa-instagram"></i>
        </div>

        <div class="search">
            
            <span> Cerca un Film o una Serie Tv</span>
            
            <!--- SearchInput ---->
            <SearchInput @term-change="setTitleFilter" @form-submit="searchProduction"/>
        </div>
    </div>



    <!----- Main ------->
    <main>


        <!-- Movies -->
        <section id="movies">

            <h2>Movies</h2>
            <div class="movies">
                <AppCard v-for="movie in store.movies" :key="movie.id" :item="movie"/>
            </div>

        </section>


        <!-- Series -->
        <section id="series">

            <h2>Series</h2>
            <div class="series">
                <AppCard v-for="serie in store.series" :key="serie.id" :item="serie"/>
            </div>
            
        </section>
    </main>

</template>







<!---------------Style -------------->

<style lang=scss scoped>

    @use '../assets/scss/vars' as *;



    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }


    .social {

        display: flex;
        align-items: center;
    }


    img {
        width: 150px;
    }

    i {
        color: white;
        font-size: 40px;
        margin-left: 40px;
    }

    h2 {
        font-size: 50px;
        text-align: center;
        color: white;
    }


    main {
        margin-top: 50px;

    }

    .movies,.series {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        margin-top: 20px;
        margin-bottom: 50px;

    }


</style>
