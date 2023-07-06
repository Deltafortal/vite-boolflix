<!---------------- Script ----------------->

<script>

// Import
import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';



export default {
    components: {AppMain , AppHeader},
    data() {
        return {
            
        }
    },
    
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
