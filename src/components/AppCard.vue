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
            return this.overlay = !this.overlay
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
            <div class="flag"> 
                <span>Lingua originale :</span>
                <img class="flagIco" v-if="hasFlag" :src="imgUrl" :alt="item.original_language">
                <div v-else>{{ item.original_language }}</div>
            </div>

            <div class="vote"> 
                <span> Voto:</span>
                <i v-for="n in 5" :class="getStars(n)" class="fa-star"></i> 
            </div>
            
        </div>
        
    </div>

</template>







<!---------------Style -------------->

<style lang="scss" scoped>


.card {
    flex-basis: calc(100% / 5);
    position: relative;
    width: 342px;
    height: 513px;
    margin: 10px;
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
    height: 100%;
    width: 342px;
    padding: 40px;
    text-align: center;
    background-color: rgba(0, 0, 0, 0.850);
    color: white;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    display: none;

}

h2 {
    font-size: 30px;
}

.flag {

    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 50px;

    .flagIco {
        width: 50px;
    }
}

span {
        font-size: 26px;
}

.vote {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

i {
    font-size: 20px;
}

h4 {
    margin-top: 30px;
    margin-bottom: 48px;
}

.content.overlay {
    display: block;
}

</style>

