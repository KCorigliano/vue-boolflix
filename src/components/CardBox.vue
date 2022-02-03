<template>
    <div class="card-container" @mouseover="hover=true" @mouseleave="hover=false">
        <div class="background" v-show="!hover">
            <p v-if="!background">Nessuna immagine</p>
            <img v-else :src="'https://image.tmdb.org/t/p/w500/'+background" alt="">
        </div>
        <div class="text" v-show="hover">
            <p><span>Titolo:</span> {{title}}</p>
            <p><span>Titolo originale:</span> {{originalTitle}}</p>
            <p><span>Lingua:</span> {{lang}}</p>
            <p><span>Voto:</span> {{vote}}</p>
            <p v-if="!overview"><span>Overview:</span> Descrizione non disponibile</p>
            <p v-else><span>Overview:</span> {{overview}}</p>
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
        lang: String,
    },
    
}
</script>

<style lang="scss" scoped>
.card-container{
    width: calc((100% / 5) - 15px);
    margin: 0 15px 15px 0;
    cursor: pointer;
    height: 320px;

    .background{
        min-height: 320px;
        z-index: 1000;
        text-align: center;
        line-height: 320px;
        
        p{
            background-color: black;
            color: white;
            font-size: 25px;
            height: 320px;
            padding: 0 12px;
        }

        img{
            width: 100%;
            min-height: 320px;
            object-fit: cover;
        }
    }

    .text{
        padding: 15px;
        color: white;
        background-color: black;
        border: 2px solid white;
        height: 320px;
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