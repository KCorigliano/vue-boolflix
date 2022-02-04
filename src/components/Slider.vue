<template>
    <div class="card-container" 
        @mouseover="stopAutoplay()"
        @mouseleave="startAutoplay()">
        <img :src="'https://image.tmdb.org/t/p/w500/'+background" alt="">
    </div>
</template>

<script>
export default {
    props:{
        background: String,
    },
    methods: {
        stopAutoplay(){
            this.$emit('stopAutoplay')
        },
        startAutoplay(){
            this.$emit('startAutoplay')
        }
    },
}
</script>

<style lang="scss" scoped>
.card-container{
    width: 450px;
    height: 650px;

    img{
        width: 100%;
        object-fit: cover;
        object-position: 50%;
    }

}
</style>