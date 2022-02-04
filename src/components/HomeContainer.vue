<template>
    <div class="container">
        <h1>Film popolari al momento</h1>
        <div class="row">
            <div @click="nextImage()"><font-awesome-icon class="arrow" icon="chevron-left" /></div>
            <slider 
                :title="popularFilm[counterClick].title" 
                :originalTitle="popularFilm[counterClick].original_title" 
                :lang="popularFilm[counterClick].original_language"
                :vote="popularFilm[counterClick].vote_average" 
                :overview="popularFilm[counterClick].overview"
                :background="popularFilm[counterClick].poster_path" 
                :key="popularFilm[counterClick].id"
            />
            <div @click="nextImage()"><font-awesome-icon class="arrow" icon="chevron-right" /></div>
        </div>
        <div class="radio-row">
            <div class="radio" :class="i === counterClick ? 'active':''" v-for="(film,i) in popularFilm" :key="film.id"></div>
        </div>
    </div>
</template>

<script>
import Slider from './Slider.vue'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faChevronRight } from '@fortawesome/free-solid-svg-icons'
import { faChevronLeft } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faChevronRight);
library.add(faChevronLeft);

export default {
    components:{
        Slider,
        FontAwesomeIcon,
    },
    props:{
        popularFilm: Array,
    },
    data() {
        return {
            counterClick: 0,
        }
    },
    methods: {
        nextImage(){
            this.counterClick++
            if(this.counterClick >=20){
                this.counterClick=0;
            }
        },
        prevImage(){
            this.counterClick--
            if(this.counterClick <0){
                this.counterClick=20;
            }
        }
    },
}
</script>

<style lang="scss" scoped>
.container{
    min-height: calc(100vh - 50px);
    width: 100%;
    margin: 0 auto;
    padding: 0 50px;
    color: white;
    text-align: center;

    h1{
        margin-bottom: 15px;
        margin-top: 0;
    }

    .row{
        display: flex;
        justify-content: space-between;
        align-items: center;
        overflow: hidden;
        height: 750px;
        margin-bottom: 25px;

        .arrow{
            color: white;
            font-size: 32px;
            cursor: pointer;

            &:hover{
                color: red;
            }
        }
    }
    
    .radio-row{
        display: flex;
        justify-content: center;

        .radio{
            background-color: white;
            width: 15px;
            height: 15px;
            border-radius: 50%;
            margin: 0 10px;
        }

        .active{
            background-color: red;
            border: 2px solid white;
            box-shadow: 0 0 5px red;
        }
    }

}
</style>