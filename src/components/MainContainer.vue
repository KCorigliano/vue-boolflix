<template>
    <div class="container">
        <h1>Film:</h1>
        <div class="row">
            <card-box 
                v-for="film in filmList"
                :title="film.name" 
                :originalTitle="film.original_name" 
                :lang="film.original_language"
                :vote="film.vote_average" 
                :overview="film.overview"
                :background="film.poster_path" 
                :key="film.id"
            />
        </div>

        <h1>Serie TV:</h1>
        <div class="row">
            <card-box 
                v-for="serie in seriesList"
                :title="serie.name" 
                :originalTitle="serie.original_name" 
                :lang="serie.original_language"
                :vote="serie.vote_average" 
                :overview="serie.overview"
                :background="serie.poster_path" 
                :key="serie.id"
            />
        </div>
    </div>
</template>

<script>
import CardBox from './CardBox.vue'

export default {
    components:{
        CardBox,
    },
    props:{
        filmList: Array,
        seriesList: Array,
    }
}
</script>

<style lang="scss" scoped>

.container{
    min-height: calc(100vh - 50px);
    width: 1200px;
    margin: 0 auto;
    padding: 15px 0;
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