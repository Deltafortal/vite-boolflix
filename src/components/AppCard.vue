<!---------------- Script ----------------->

<script>


export default {

    data() {
        return {
            posterUri: 'https://image.tmdb.org/t/p/w342'
        }
    },

    props: {

        item: Object,
    },

    computed: {
        hasFlag() {
            const flags = ['it', 'en'];
            return flags.includes(this.item.original_language)
        },

        imgUrl() {
            const url = new URL (`../assets/img/${this.item.original_language}.png`, import.meta.url);
            return url.href
        }
    }

};

</script>








<!--------------- Template ------------->

<template>
  
    <div class="card">

        <img class="poster" :src="`${posterUri}${item.poster_path}`" :alt="item.title || item.name">

        <h2>{{ item.title || item.name }}</h2>
        <h4> {{ item.original_title || item.original_name }}</h4>
        <div> 
            <img v-if="hasFlag" :src="imgUrl" :alt="item.original_language">
            <div v-else>{{ item.original_language }}</div>
        </div>
        <div> {{ item.vote_average }}</div>
        
    </div>

</template>







<!---------------Style -------------->

<style lang="scss" scoped>


.card {
    position: relative;
    width: 300px;
    height: 400px;
}
.poster {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;

}

</style>
