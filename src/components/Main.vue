<template>
  <div class="p-3">
    <h5 class="text-secondary mb-4" v-if="searchText.length != 0">Hai cercato: {{searchText}}</h5>
    
      <h5 class="text-secondary">Movies:</h5>
      <div v-for="movie in movies" :key="movie.id">
        <div class="mb-4">
          <div>
            <strong>Titolo: </strong>
            {{movie.title}}
          </div>
          <div>
            <strong>Titolo originale: </strong>
            {{movie.original_title}}
          </div>
          <div>
            <strong>Lingua: </strong>
            {{movie.original_language}}
          </div>
          <div>
            <strong>Voto: </strong>
            {{movie.vote_average}}
          </div>
        </div>
      </div>
    
    
      <h5 class="text-secondary">TV Shows:</h5>
      <div v-for="serie in series" :key="serie.id">
        <div class="mb-4">
          <div>
            <strong>Titolo: </strong>
            {{serie.name}}
          </div>
          <div>
            <strong>Titolo originale: </strong>
            {{serie.original_name}}
          </div>
          <div>
            <strong>Lingua: </strong>
            {{serie.original_language}}
          </div>
          <div>
            <strong>Voto: </strong>
            {{serie.vote_average}}
          </div>
        </div>
      </div>
   
  </div>
</template>

<script>

export default {
    name: 'Main',
    props:{
      movies: Array,
      series: Array,
      searchText: String,
    }
    
}
</script>

<style lang="scss" scoped>

</style>