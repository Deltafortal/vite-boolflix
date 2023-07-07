<!---------------- Script ----------------->

<script>


export default {

    data() {
        return {
            posterUri: 'https://image.tmdb.org/t/p/w342',
            overlay: false,
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
        },
        getVote() {
            return Math.ceil(this.item.vote_average / 2)
        },
        addOverlay() {

            if(this.overlay === true) {
                return 'overlay';
            } else {
                return '';
            }

        }
        
    },
    methods: {
        getStars(n) {
            return n <= this.getVote ? 'fas' : 'far'
        },

        toggleOverlay() {
            return this.overlay != this.overlay
        }
    }
    

};

</script>








<!--------------- Template ------------->

<template>
  
    <div class="card" @mouseover="toggleOverlay" @mouseleave="toggleOverlay">

        <img class="poster" :src="`${posterUri}${item.poster_path}`" :alt="item.title || item.name">
        
        <div class="content" :class="addOverlay">
            <h2>{{ item.title || item.name }}</h2>
            <h4> {{ item.original_title || item.original_name }}</h4>
            <div> 
                <img v-if="hasFlag" :src="imgUrl" :alt="item.original_language">
                <div v-else>{{ item.original_language }}</div>
            </div>

            <div> <i v-for="n in 5" :class="getStars(n)" class="fa-star"></i> </div>
            
        </div>
        
    </div>

</template>







<!---------------Style -------------->

<style lang="scss" scoped>


.card {
    flex-basis: 25%;
    position: relative;
    width: 342px;
    height: 513px;
    margin-bottom: 20px;
    cursor: pointer;
}
.poster {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;

}

.content {
    display: none;
    background-color: rgba(0, 0, 0, 0.603);
    color: white;
    height: 100%;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;

    .img {
        width: 60px;
    }
}


.content.overlay {
    display: block;
}

</style>

