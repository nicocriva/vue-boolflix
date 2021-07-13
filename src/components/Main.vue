<template>
  <div class="p-3">
    <div v-if="movieTitle.length != 0">Hai cercato: {{movieTitle}}</div>
    <div v-if="movieTitle.length != 0" class="float-start">
      <div>{{movieTitle}}</div>
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
        movie: '', 
        
      }
    },
    created(){
      this.getInfo();
    },
    methods: {
      getInfo(){
        axios
          .get(this.apiURL + this.apiKey + this.language + this.query + this.movieTitle)
          .then(element => {
            console.log(element.data.results);
          })
      }
    }
    
}
</script>

<style lang="scss" scoped>

</style>