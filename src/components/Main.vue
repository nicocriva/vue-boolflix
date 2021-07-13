<template>
  <div class="p-3">
    <h5 class="text-secondary" v-if="movieTitle.length != 0">Hai cercato: {{movieTitle}}</h5>
    <div v-if="movieTitle.length != 0" class="float-start">
      <div v-for="(item, index) in movie" :key="index">
        <div class="my-4">
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
      movieTitle: String,
    },
    data(){
      return{
        apiURL: 'https://api.themoviedb.org/3/search/movie',
        apiKey: '?api_key=af93f11867caf2fb3e44dfe407851a1d',
        language: '&language=it-IT',
        query: '&query=',
        movie: [], 
        
      }
    },
    updated(){
      this.getInfo();
    },
    methods: {
      getInfo(){
        if(this.movieTitle != ''){
          axios
            .get(this.apiURL + this.apiKey + this.language + this.query + this.movieTitle)
            .then(element => {
              this.movie = element.data.results;
              })

        }
      }
    }
    
}
</script>

<style lang="scss" scoped>

</style>