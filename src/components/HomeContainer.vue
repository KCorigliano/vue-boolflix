<template>
    <div class="container">
        <h1>Recommended films</h1>
        <div class="row">
            <div @click="prevImage()"><font-awesome-icon class="arrow" icon="chevron-left" /></div>
            <slider 
                class="jumbo-img"
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
@import '@/style/homeContainer.scss'
</style>