<template>
  <div class="p-3">
    <div v-if="movieTitle.length != 0">Hai cercato: {{movieTitle}}</div>
    <div v-if="movieTitle.length != 0" class="float-start">
      <img :src="'https://image.tmdb.org/t/p/w300' + movieImg" alt="Movie poster">
    </div>
      
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Main',
    props:{
      movieTitle: String,
    },
    data(){
      return{
        apiURL: `https://api.themoviedb.org/3/search/movie?api_key=af93f11867caf2fb3e44dfe407851a1d&language=it-IT&query=${this.movieTitle}`,
        movieImg: [],
        counter: 0,
      }
    },
    created(){
      this.getImg();
    },
    methods: {
      getImg(){
        axios
          .get(this.apiURL, this.title)
          .then(element => {
            this.movieImg = element.data.results[this.counter].poster_path;
            console.log(element.data.results);
          })
      }
    }
    
}
</script>

<style lang="scss" scoped>

</style>