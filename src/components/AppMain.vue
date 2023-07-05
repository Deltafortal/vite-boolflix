<!---------------- Script ----------------->

<script>

// Import
import SearchInput from './SearchInput.vue';
import { store } from '../data/store';


export default {
    components: {SearchInput},
    data() {
        return {store}
    }
}


</script>








<!--------------- Template ------------->

<template>
  
    <!--- SearchInput ---->
    <SearchInput />


    <!----- Main ------->
    <main>


    </main>

</template>







<!---------------Style -------------->

<style scoped>



</style>
