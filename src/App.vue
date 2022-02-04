<template>
  <div id="app">
    <header-box 
      @searchFilm="searchButton"
      @homeClick="homeClick"
      @serieClick="serieClick"
      @filmClick="filmClick"
    />
    <main-container 
      :filmList="searchedFilm" 
      :popularFilm="popularFilm"
      :recommendedFilm="recommendedFilm"
      :oncomingFilm="oncomingFilm"
      :seriesList="searchedSeries" 
      :popularSeries="popularSeries" 
      :recommendedSeries="recommendedSeries" 
      :ratedSeries="ratedSeries" 
      :firstResearch="firstResearch"
      :homeBool="homeBool"
      :serieBool="serieBool"
      :filmBool="filmBool"
    />
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
      popularFilm: [],
      oncomingFilm: [],
      searchedSeries: [],
      popularSeries: [],
      ratedSeries: [],
      firstResearch: false,
      homeBool:true,
      serieBool:false,
      filmBool:false,
      api_key:'846025be620b599134a99b863faca32c&language=en-US&page=1',
      videoSpiderman: [],
    }
  },
  mounted(){
    // Popular film
    axios.get('https://api.themoviedb.org/3/movie/popular?api_key=846025be620b599134a99b863faca32c&language=en-US&page=1').then((response) =>{
      this.popularFilm = response.data.results;
    });
    // Oncoming film
    axios.get('https://api.themoviedb.org/3/movie/upcoming?api_key=846025be620b599134a99b863faca32c&language=en-US&page=1').then((response) =>{
      this.oncomingFilm = response.data.results;
    });
    // Popular serie
    axios.get('https://api.themoviedb.org/3/tv/popular?api_key=846025be620b599134a99b863faca32c&language=en-US&page=1').then((response) =>{
      this.popularSeries = response.data.results;
    });
    // Most rated serie
    axios.get('https://api.themoviedb.org/3/tv/top_rated?api_key=846025be620b599134a99b863faca32c&language=en-US&page=1').then((response) =>{
      this.ratedSeries = response.data.results;
    });
  },
  methods: {
    // Api for the search button
    searchButton(filmTitle){
      // Film api

      const params = {
        query: filmTitle,
        api_key:this.api_key
      }

      axios.get('https://api.themoviedb.org/3/search/movie?query=',{params}).then((response) =>{
          this.searchedFilm = response.data.results;
      });
      // Serie TV api
      axios.get('https://api.themoviedb.org/3/search/tv?query=',{params}).then((response) =>{
          this.searchedSeries = response.data.results;
      })
      this.firstResearch=true;
    },
    homeClick(){
      this.homeBool=true;
      this.serieBool=false;
      this.filmBool=false;
    },
    serieClick(){
      this.homeBool=false;
      this.serieBool=true;
      this.filmBool=false;
    },
    filmClick(){
      this.homeBool=false;
      this.serieBool=false;
      this.filmBool=true;
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
  background-color: #141414;
  font-family: Arial, Helvetica, sans-serif;

  /* width */
  ::-webkit-scrollbar {
      width: 5px;
  }

  /* Track */
  ::-webkit-scrollbar-track {
      border-radius: 5px;
  }

  /* Handle */
  ::-webkit-scrollbar-thumb {
      background: grey;
      border-radius: 10px;
  }
}

</style>
