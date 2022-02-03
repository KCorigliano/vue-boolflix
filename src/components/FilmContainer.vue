<template>
    <div class="container">
        <div v-if="firstResearch">
            <h1>Film cercati:</h1>
            <div class="row">
                <card-box 
                    v-for="film in filmList"
                    :title="film.title" 
                    :originalTitle="film.original_title" 
                    :lang="film.original_language"
                    :vote="film.vote_average" 
                    :overview="film.overview"
                    :background="film.poster_path" 
                    :key="film.id"
                />
            </div>
        </div>



        <h1>Film più popolari:</h1>
        <div class="row">
            <card-box 
                v-for="film in popularFilm"
                :title="film.title" 
                :originalTitle="film.original_title" 
                :lang="film.original_language"
                :vote="film.vote_average" 
                :overview="film.overview"
                :background="film.poster_path" 
                :key="film.id"
            />
        </div>

        <h1>Film in arrivo:</h1>
        <div class="row">
            <card-box 
                v-for="film in oncomingFilm"
                :title="film.title" 
                :originalTitle="film.original_title" 
                :lang="film.original_language"
                :vote="film.vote_average" 
                :overview="film.overview"
                :background="film.poster_path" 
                :key="film.id"
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
        popularFilm: Array,
        oncomingFilm: Array,
        firstResearch: Boolean,
    }
}
</script>

<style lang="scss" scoped>
.container{
    min-height: calc(100vh - 50px);
    width: 100%;
    margin: 0 auto;
    padding: 15px 50px;
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