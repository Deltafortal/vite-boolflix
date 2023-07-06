<!---------------- Script ----------------->

<script>


export default {
    props: {

        item: Object
    },


    
};

</script>








<!--------------- Template ------------->

<template>
  
    <h2>{{ item.title || item.name }}</h2>
    <h4> {{ item.original_title || item.original_name }}</h4>
    <div> {{ item.original_language }}</div>
    <div> {{ item.vote_average }}</div>


</template>







<!---------------Style -------------->

<style lang="scss">



</style>
