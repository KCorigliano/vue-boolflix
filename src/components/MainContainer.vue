<template>
    <div class="container">
        <card-box 
            :title="filmList[0].name" 
            :originalTitle="filmList[0].original_name" 
            :vote="filmList[0].vote_average" 
            :overview="filmList[0].overview"
            :background="filmList[0].poster_path" />
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
}
</style>