<template>
  <div class="p-3">
    <h5 class="text-secondary mb-4" v-if="searchText.length != 0">Hai cercato: {{searchText}}</h5>
    <div v-if="searchText.length != 0">
      <h5 class="text-secondary">Movies:</h5>
      <div v-for="(item, index) in movie" :key="index">
        <div class="mb-4">
          <div><strong>Titolo: </strong>{{item.title}}</div>
          <div><strong>Titolo originale: </strong>{{item.original_title}}</div>
          <div><strong>Lingua: </strong>{{item.original_language}}</div>
          <div><strong>Voto: </strong>{{item.vote_average}}</div>
        </div>
      </div>
    </div>
    <div v-if="searchText.length != 0">
      <h5 class="text-secondary">TV Shows:</h5>
      <div v-for="(item, index) in serie" :key="index">
        <div class="mb-4">
          <div><strong>Titolo: </strong>{{item.title}}</div>
          <div><strong>Titolo originale: </strong>{{item.original_title}}</div>
          <div><strong>Lingua: </strong>{{item.original_language}}</div>
          <div><strong>Voto: </strong>{{item.vote_average}}</div>
        </div>
      </div>
    </div>
      
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Main',
    props:{
      searchText: String,
    },
    data(){
      return{
        movieApiURL: 'https://api.themoviedb.org/3/search/movie',
        serieApiURL: 'https://api.themoviedb.org/3/search/tv',
        apiKey: '?api_key=af93f11867caf2fb3e44dfe407851a1d',
        language: '&language=it-IT',
        query: '&query=',
        movie: [],
        serie: [],
        
      }
    },
    created(){
      this.getMovieInfo();
      this.getSerieInfo();
    },
    methods: {
      getMovieInfo(){
        axios
          .get(this.movieApiURL + this.apiKey + this.language + this.query + this.searchText)
          .then(element => {
            this.movie = element.data.results;
            })

      },
      getSerieInfo(){
        axios
          .get(this.serieApiURL + this.apiKey + this.language + this.query + this.searchText)
          .then(element => {
            this.serie = element.data.results;
            })

      }
    }
    
}
</script>

<style lang="scss" scoped>

</style>