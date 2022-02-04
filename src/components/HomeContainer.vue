<template>
    <div class="container">
        <h1>Film consigliati</h1>
        <div class="row">
            <div @click="prevImage()"><font-awesome-icon class="arrow" icon="chevron-left" /></div>
            <slider 
                :background="popularFilm[counterClick].poster_path" 
                @startAutoplay="startAutoplay"
                @stopAutoplay="stopAutoplay"
            />
            <div @click="nextImage()"><font-awesome-icon class="arrow" icon="chevron-right" /></div>
        </div>
        <!-- <div class="radio-row">
            <div class="radio" :class="i === counterClick ? 'active':''" v-for="(film,i) in popularFilm" :key="film.id"></div>
        </div> -->
        <div class="radio-row">
            <slider-background 
                @currentImage="currentImage(i)"
                class="clickable"
                v-for="(film, i) in popularFilm"
                :background="film.poster_path"
                :key="i"
                :class="i === counterClick ? 'active':'not-active'"
            />
        </div>
    </div>
</template>

<script>
import Slider from './Slider.vue'
import SliderBackground from './SliderBackgound.vue'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faChevronRight } from '@fortawesome/free-solid-svg-icons'
import { faChevronLeft } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faChevronRight);
library.add(faChevronLeft);

export default {
    components:{
        Slider,
        SliderBackground,
        FontAwesomeIcon,
    },
    props:{
        popularFilm: Array,
    },
    data() {
        return {
            counterClick: 0,
            stopplay: this.interval,
            statusAutoPlay: true,
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
        },
        currentImage(i){
            this.counterClick = i;
        },
        startAutoplay: function(){
            this.interval = setInterval(() => this.nextImage(), 5000);
        },
        stopAutoplay: function(){
            clearInterval(this.interval);
            this.statusAutoPlay = false;
        },
    },
    mounted: function(){
        this.startAutoplay();
    }
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
        height: 650px;
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
        align-items: baseline;
        overflow-x: visible;

        .clickable{
            cursor: pointer;
        }

        .active{
            border: 2px solid white;
            height: 150px;
            width: 175px;
            filter: brightness(175%);
        }

        .not-active{
            height: 150px;
            width: 150px;
            filter: brightness(50%);
        }
    }

}
</style>