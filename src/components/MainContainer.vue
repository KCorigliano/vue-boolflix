<template>
    <div class="container">
        <card-box 
            v-for="(film, index) in filmList"
            :title="film.name" 
            :originalTitle="film.original_name" 
            :lang="film.original_language"
            :vote="film.vote_average" 
            :overview="film.overview"
            :background="film.poster_path" 
            :key="index"/>
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
    }
}
</script>

<style lang="scss" scoped>
.container{
    min-height: calc(100vh - 50px);
    width: 1200px;
    margin: 0 auto;
    padding: 50px 25px;
    display: flex;
    flex-wrap: wrap;
}
</style>