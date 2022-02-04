<template>
    <div class="card-container">
        <img :src="'https://image.tmdb.org/t/p/w500/'+background" alt="">
    </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faStar } from '@fortawesome/free-solid-svg-icons'
// import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faStar);

export default {
    components:{
        // FontAwesomeIcon,
    },
    data() {
        return {
            starVote: [],
        }
    },
    props:{
        title: String,
        originalTitle: String,
        vote: Number,
        overview: String,
        background: String,
        lang: String,
    },mounted() {
        this.newVote(this.vote);
    },
    methods: {
        newVote(vote){
            const fiveVote = Math.round((vote * 5 / 10));
            for (let i=0; i <= fiveVote; i++){
                this.starVote.push(fiveVote);
            }
        }
    },
    
}
</script>

<style lang="scss" scoped>
.card-container{
    width: 500px;
    height: 750px;

    img{
        width: 100%;
        object-fit: cover;
        object-position: 50%;
    }

}
</style>