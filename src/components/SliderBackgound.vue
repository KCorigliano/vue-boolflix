<template>
    <div class="card-container">
        <img @click="currentImage()" :src="'https://image.tmdb.org/t/p/w500/'+background" alt="">
    </div>
</template>

<script>
export default {
    props:{
        background: String,
    },
    methods: {
        currentImage(){
            this.$emit('currentImage')
        }
    },
}
</script>

<style lang="scss" scoped>
.card-container{
    width: 125px;
    height: 130px;

    img{
        width: 100%;
        object-fit: cover;
        object-position: 50%;
    }
}
</style>