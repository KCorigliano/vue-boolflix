<template>
    <div class="container">
        <home-container 
            :popularFilm="popularFilm"
            v-if="homeBool"
        />

        <film-container 
            :filmList="filmList" 
            :popularFilm="popularFilm"
            :recommendedFilm="recommendedFilm"
            :oncomingFilm="oncomingFilm"
            :firstResearch="firstResearch"
            v-if="filmBool"
        />

        <series-container 
            :seriesList="seriesList" 
            :popularSeries="popularSeries" 
            :recommendedSeries="recommendedSeries" 
            :ratedSeries="ratedSeries"
            :firstResearch="firstResearch"
            v-if="serieBool"
        />
    </div>
</template>

<script>
import FilmContainer from './FilmContainer.vue'
import SeriesContainer from './SeriesContainer.vue'
import HomeContainer from './HomeContainer.vue'

export default {
    components:{
        FilmContainer,
        SeriesContainer,
        HomeContainer
    },
    props:{
        filmList: Array,
        popularFilm: Array,
        oncomingFilm: Array,
        popularSeries: Array,
        ratedSeries: Array,
        seriesList: Array,
        firstResearch: Boolean,
        homeBool: Boolean,
        serieBool: Boolean,
        filmBool: Boolean,
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

    .row{
        display: flex;
        overflow: hidden;
        height: 370px;
        margin-bottom: 15px;

        &:hover{
            overflow: scroll;
            overflow-y: hidden;
        }
    }
    
}
</style>