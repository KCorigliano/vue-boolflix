<template>
  <div id="app">
    <header-box @searchFilm="searchButton"/>
    <main-container :filmList="searchedFilm" :seriesList="searchedSeries"/>
  </div>
</template>

<script>
import axios from 'axios'
import MainContainer from './components/MainContainer.vue'
import HeaderBox from './components/HeaderBox.vue'

export default {
  name: 'App',
  components: {
    MainContainer,
    HeaderBox,
  },
  data() {
    return {
      searchedFilm: [],
      searchedSeries: [],
    }
  },
  methods: {
    searchButton(filmTitle){
      axios.get('https://api.themoviedb.org/3/search/movie?query='+filmTitle+'&api_key=846025be620b599134a99b863faca32c').then((response) =>{
          this.searchedFilm = response.data.results;
      });
      axios.get('https://api.themoviedb.org/3/search/tv?query='+filmTitle+'&api_key=846025be620b599134a99b863faca32c').then((response) =>{
          this.searchedSeries = response.data.results;
      })
    }
  },
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app{
  background-color: grey;
}
</style>
