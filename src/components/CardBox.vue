<template>
    <div class="card-container" @mouseover="hover=true" @mouseleave="hover=false">
        <div class="background" v-show="!hover">
            <p v-if="!background">Nessuna immagine</p>
            <img v-else :src="'https://image.tmdb.org/t/p/w500/'+background" alt="">
        </div>
        <div class="text" v-show="hover">
            <p><span>Title: </span>{{title}}</p>
            <p v-if="originalTitle != title"><span>Original title: </span>{{originalTitle}}</p>
            <div class="genre">Genres: 
                <p v-for="(generi, i) in genre" :key="i">- {{genre[i].name}}</p>
            </div>
            <p><span>Leanguage: </span><lang-flag :iso="lang" :squared="false"/></p>
            <p><span>Votes: </span><star-vote :vote="vote"/></p>
            <p v-if="!overview"><span>Overview:</span> Description not avaible</p>
            <p v-else><span>Overview:</span> {{overview}}</p>
        </div>
    </div>
</template>

<script>
import StarVote from './StarVote.vue'
import axios from 'axios'
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
            filmDetail: [],
            genre: [],
        }
    },
    props:{
        title: String,
        originalTitle: String,
        vote: Number,
        overview: String,
        background: String,
        lang: String,
        filmID: Number,
        type: String,
    }, 
    mounted() {
        this.getGenre();
    },
    methods: {
        async getGenre(){
            this.genre = await this.genresArray()
        },
        async genresArray(){
            const result = await axios.get(`https://api.themoviedb.org/3/${this.type}/${this.filmID}?&api_key=846025be620b599134a99b863faca32c&language=en-US`).then((response) =>{
                return response.data.genres;
            });
            return result
        }
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

        .genre{
            font-weight: bold;
            margin: 15px 0;

            p{
                font-weight: 400;
                margin: 5px;
            }
        }
    }

}
</style>