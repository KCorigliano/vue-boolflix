<template>
    <div class="header">
        <div>
            <h1 @click="homeClick">Boolflix</h1>
            <p :class="homeBool ? 'clicked':''" @click="homeClick">Home</p>
            <p :class="serieBool ? 'clicked':''" @click="serieClick">Serie TV</p>
            <p :class="filmBool ? 'clicked':''" @click="filmClick">Film</p>
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
        }
    },
    props:{
        homeBool: Boolean,
        serieBool: Boolean,
        filmBool: Boolean,
        searchInput: Boolean,
    },
    methods: {
        searchFilm(){
            this.$emit('searchFilm', this.filmTitle, this.searchInput);
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
@import '@/style/headerBox.scss'
</style>