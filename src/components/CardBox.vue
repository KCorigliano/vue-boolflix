<template>
    <div class="card-container" @mouseover="hover = false" @mouseleave="hover = true">
        <div class="background" v-if="hover">
            <img :src="'https://image.tmdb.org/t/p/w500/'+background" alt="">
        </div>
        <div class="text" v-else>
            <p><span>Titolo:</span> {{title}}</p>
            <p><span>Titolo originale:</span> {{originalTitle}}</p>
            <p><span>Voto:</span> {{vote}}</p>
            <p><span>Overview:</span> {{overview}}</p>
        </div>
        
    </div>
</template>

<script>
export default {
    data() {
        return {
            hover: false,
        }
    },
    props:{
        title: String,
        originalTitle: String,
        vote: Number,
        overview: String,
        background: String,
    },
    
}
</script>

<style lang="scss" scoped>
.card-container{
    width: calc(100% / 5);
    margin: 0 15px 0 0;
    cursor: pointer;

    .background{
        img{
            width: 100%;
        }
    }

    .text{
        padding: 15px;
        color: white;
        background-color: black;
        border: 2px solid white;
        height: 345px;
        overflow: auto;

        p{
            margin-bottom: 15px;

            span{
                font-weight: bold;
            }
        }
    }

}
</style>