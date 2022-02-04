<template>
    <div class="header">
        <div>
            <h1 @click="homeClick">Boolflix</h1>
            <p :class="newHomeBool ? 'clicked':''" @click="homeClick">Home</p>
            <p :class="newSerieBool ? 'clicked':''" @click="serieClick">Serie TV</p>
            <p :class="newFilmBool ? 'clicked':''" @click="filmClick">Film</p>
        </div>
        <div>
            <div v-if="searchInput">
                <input type="text" v-model="filmTitle" placeholder="Cerca un film" @keyup.enter="searchFilm">
                <button @click="searchFilm">Search</button>
            </div>
            <font-awesome-icon class="search-icon" icon="search" @click="searchInputShow" />
            <div class="user"></div>
            <font-awesome-icon icon="chevron-down" />
        </div>
    </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faSearch } from '@fortawesome/free-solid-svg-icons'
import { faChevronDown } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faSearch);
library.add(faChevronDown);

export default {
    components:{
        FontAwesomeIcon,
    },
    data() {
        return {
            filmTitle: '',
            homeBool: true,
            serieBool: false,
            filmBool: false,
            searchInput: false
        }
    },
    props:{
        newHomeBool: Boolean,
        newSerieBool: Boolean,
        newFilmBool: Boolean,
    },
    methods: {
        searchFilm(){
            this.$emit('searchFilm', this.filmTitle);
        },
        homeClick(){
            this.$emit('homeClick', this.homeBool, this.serieBool, this.filmBool)
        },
        serieClick(){
            this.$emit('serieClick', this.homeBool, this.serieBool, this.filmBool)
        },
        filmClick(){
            this.$emit('filmClick', this.homeBool, this.serieBool, this.filmBool)
        },
        searchInputShow(){
            this.searchInput = !this.searchInput
        }
    },
}
</script>

<style lang="scss" scoped>
.header{

    ::placeholder{
        color: white;
    }

    display: flex;
    justify-content: space-between;
    width: 100%;
    align-items: center;
    padding: 0 15px;
    height: 50px;

    div:first-child{
        display: flex;
        align-items: center;

        h1{
            color: red;
            text-transform: uppercase;
            margin-right: 50px;
            cursor: pointer;
        }
    
        p{
            color: white;
            margin-right: 0;
            padding: 0 10px;
            transition: all 0.5s;

            &:hover{
                cursor: pointer;
                border-bottom: 2px solid red;
                padding-bottom: 4px;
                font-weight: bold;
                font-size: 18px;
                transition: all 0.5s;
            }
        }

        .clicked{
            border-bottom: 2px solid red;
            padding-bottom: 4px;
            font-weight: bold;
            font-size: 18px;
        }
    }

    div{
        input{
            margin: 0 15px;
        }

        button{
            cursor: pointer;
        }
    }

    div{
        display: flex;
        align-items: center;
        color: white;

        

        div{
            margin-right: 15px;

            input,
            button{
                background-color: rgb(80, 80, 80);
                color: white;
                border: none;
                border-radius: 15px;
                padding: 5px 10px;
            }
        }

        .search-icon{
            cursor: pointer;
        }

        .user{
            width: 40px;
            height: 40px;
            background-color: greenyellow;
            margin: 15px;
        }
    }
  
}
</style>