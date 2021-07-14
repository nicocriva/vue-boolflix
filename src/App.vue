<template>
  <div id="app">
    <Header @search="searchMovie"/>
    <Main :searchText="titolo" 
    :movies="moviesArr" :series="seriesArr"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';



export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      titolo: '',
      movieApiURL: 'https://api.themoviedb.org/3/search/movie',
      serieApiURL: 'https://api.themoviedb.org/3/search/tv',
      moviesArr: [],
      seriesArr: [],
    }
  },
  methods:{
    searchMovie(text){
      axios
          .get(this.movieApiURL, {
            params: {
              api_key: 'af93f11867caf2fb3e44dfe407851a1d',
              query: text,
              language: 'it-IT'
            }
          })
          .then(element => {
            this.moviesArr = element.data.results;
            })

      axios
          .get(this.serieApiURL, {
            params: {
              api_key: 'af93f11867caf2fb3e44dfe407851a1d',
              query: text,
              language: 'it-IT'
            }
          })
          .then(element => {
            this.seriesArr = element.data.results;
            console.log(this.moviesArr, this.seriesArr);

          })
    }
  }
}
</script>

<style lang="scss">
@import 'bootstrap';
@import './style/commons.scss';

</style>
