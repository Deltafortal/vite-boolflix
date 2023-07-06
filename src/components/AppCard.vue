<!---------------- Script ----------------->

<script>


export default {
    props: {

        item: Object
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
  
    <h2>{{ item.title || item.name }}</h2>
    <h4> {{ item.original_title || item.original_name }}</h4>
    <div> 
        <img v-if="hasFlag" :src="imgUrl" :alt="item.original_language">
        <div v-else>{{ item.original_language }}</div>
    </div>
    <div> {{ item.vote_average }}</div>


</template>







<!---------------Style -------------->

<style lang="scss">



</style>
