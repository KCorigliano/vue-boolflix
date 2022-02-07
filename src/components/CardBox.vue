<template>
    <div class="card-container" @mouseover="hover=true" @mouseleave="hover=false">
        <div class="background" v-show="!hover">
            <p v-if="!background">Nessuna immagine</p>
            <img v-else :src="'https://image.tmdb.org/t/p/w500/'+background" alt="">
        </div>
        <div class="text" v-show="hover">
            <p><span>Titolo: </span>{{title}}</p>
            <p v-if="originalTitle != title"><span>Titolo originale: </span>{{originalTitle}}</p>
            <p><span>Lingua: </span><lang-flag :iso="lang" :squared="false"/></p>
            <p><span>Voto: </span><star-vote :vote="vote"/></p>
            <p v-if="!overview"><span>Overview:</span> Descrizione non disponibile</p>
            <p v-else><span>Overview:</span> {{overview}}</p>
        </div>
    </div>
</template>

<script>
import StarVote from './StarVote.vue'

import LangFlag from 'vue-lang-code-flags';


export default {
    components:{
        StarVote,
        LangFlag
    },
    data() {
        return {
            hover: false,
            starVote: [],
        }
    },
    props:{
        title: String,
        originalTitle: String,
        vote: Number,
        overview: String,
        background: String,
        lang: String,
        genre: String,
    },
}
</script>

<style lang="scss" scoped>
.card-container{
    min-width: 225px;
    max-width: 225px;
    margin: 10px 5px 15px 0;
    cursor: pointer;
    height: 320px;

    .background{
        min-height: 320px;
        text-align: center;
        line-height: 320px;
        border-radius: 5px;
        
        p{
            background-color: black;
            color: white;
            font-size: 23px;
            height: 320px;
            padding: 0 12px;
        }

        img{
            width: 100%;
            height: 320px;
            object-fit: cover;
            border-radius: 5px;
        }
    }

    .text{
        padding: 15px;
        color: white;
        background-color: black;
        border: 2px solid white;
        height: 320px;
        overflow-y: auto;
        border-radius: 5px;

        p{
            margin-bottom: 15px;
            
            span{
                font-weight: bold;
            }
        }
    }

}
</style>