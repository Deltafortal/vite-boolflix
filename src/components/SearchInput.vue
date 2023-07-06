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

        <input type="text" v-model.trim="insertedTerm" @keyup="$emit('term-change', insertedTerm)">
        
        <input type="submit" value="cerca">
    </form>


</template>







<!---------------Style -------------->

<style scoped>



</style>
