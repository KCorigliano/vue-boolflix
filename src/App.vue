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
  mounted(){
    axios.get('https://api.themoviedb.org/3/search/movie?query='+this.randomLetter()+'&api_key=846025be620b599134a99b863faca32c').then((response) =>{
      this.searchedFilm = response.data.results;
    });
    axios.get('https://api.themoviedb.org/3/search/tv?query='+this.randomLetter()+'&api_key=846025be620b599134a99b863faca32c').then((response) =>{
      this.searchedSeries = response.data.results;
    })
  },
  methods: {
    // Api for the search button
    searchButton(filmTitle){
      // Film api
      axios.get('https://api.themoviedb.org/3/search/movie?query='+filmTitle+'&api_key=846025be620b599134a99b863faca32c').then((response) =>{
          this.searchedFilm = response.data.results;
      });
      // Serie TV api
      axios.get('https://api.themoviedb.org/3/search/tv?query='+filmTitle+'&api_key=846025be620b599134a99b863faca32c').then((response) =>{
          this.searchedSeries = response.data.results;
      })
    },
    randomLetter(){
      const characters ='ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
      let result = '';
      const charactersLength = characters.length;
      for ( let i = 0; i <= 1; i++ ) {
        result = characters.charAt(Math.floor(Math.random() * charactersLength));
      }
      return result;
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
