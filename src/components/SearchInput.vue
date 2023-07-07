<!---------------- Script ----------------->

<script>


export default {
    data() {
        return {
            insertedTerm :'',
            
        }
    },

    emits: ['term-change', 'form-submit'],

    computed: {
        
    }
}


</script>








<!--------------- Template ------------->

<template>
  
    <!--- SearchBar ---->
   
    <form action="" @submit.prevent="$emit('form-submit')">

        <input class="searchbar" type="text" v-model.trim="insertedTerm" @keyup="$emit('term-change', insertedTerm)">
        
        <input class="btn" type="submit" value="cerca">
    </form>


</template>







<!---------------Style -------------->

<style lang="scss" scoped>

    @use '../assets/scss/vars' as *;



    input {
        font-size: 23px;
        padding: 10px 15px;
        border-radius: 8px;
        color: white;
        border: transparent;
        margin-left: 10px;
    }

    .searchbar {
        background-color: $secondaryCol;
    }
    
    .btn {
        background-color: $primaryCol;
    }


</style>
