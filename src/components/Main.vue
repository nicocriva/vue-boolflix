<template>
  <div class="p-3">
    <h5 class="text-secondary mb-4" v-if="searchText.length != 0">Hai cercato: {{searchText}}</h5>
    <div v-if="searchText.length != 0">
      <h5 class="text-secondary">Movies:</h5>
      <div v-for="(movie, index) in movies" :key="index">
        <div class="mb-4">
          <div>
            <strong>Titolo: </strong>
            {{movie.title}}
            </div>
          <div><strong>Titolo originale: </strong>{{movie.original_title}}</div>
          <div><strong>Lingua: </strong>{{movie.original_language}}</div>
          <div><strong>Voto: </strong>{{movie.vote_average}}</div>
        </div>
      </div>
    </div>
    <div v-if="searchText.length != 0">
      <h5 class="text-secondary">TV Shows:</h5>
      <div v-for="(serie, index) in series" :key="index">
        <div class="mb-4">
          <div><strong>Titolo: </strong>{{serie.name}}</div>
          <div><strong>Titolo originale: </strong>{{serie.original_name}}</div>
          <div><strong>Lingua: </strong>{{serie.original_language}}</div>
          <div><strong>Voto: </strong>{{serie.vote_average}}</div>
        </div>
      </div>
    </div>
      <button @click="btn">ciao</button>
  </div>
</template>

<script>

export default {
    name: 'Main',
    props:{
      movies: Array,
      series: Array,
      searchText: String,
    },
    methods:{
      btn(){
        // this.film = this.movie;
        console.log(this.movies, 'film');

      }
    }
    
}
</script>

<style lang="scss" scoped>

</style>