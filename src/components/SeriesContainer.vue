<template>
    <div class="container">
        <div v-if="firstResearch">
            <h1>Serie cercate:</h1>
            <div class="row">
                <card-box 
                    v-for="film in seriesList"
                    :title="film.name" 
                    :originalTitle="film.original_name" 
                    :lang="film.original_language"
                    :vote="film.vote_average" 
                    :overview="film.overview"
                    :background="film.poster_path" 
                    :key="film.id"
                />
            </div>
        </div>
   
 

        <h1>Serie più popolari:</h1>
        <div class="row">
            <card-box 
                v-for="film in popularSeries"
                :title="film.name" 
                :originalTitle="film.original_name" 
                :lang="film.original_language"
                :vote="film.vote_average" 
                :overview="film.overview"
                :background="film.poster_path" 
                :key="film.id"
            />
        </div>

        <h1>Serie più votate:</h1>
        <div class="row">
            <card-box 
                v-for="film in ratedSeries"
                :title="film.name" 
                :originalTitle="film.original_name" 
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
        popularSeries: Array,
        ratedSeries: Array,
        seriesList: Array,
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