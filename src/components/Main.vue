<template>
  <div class="p-3">
    <h5 class="text-secondary">Movies:</h5>
    <div v-for="movie in movies" :key="movie.id">
      <div class="mb-4">
        <div>
          <strong>Titolo: </strong> {{movie.title}}
        </div>
        <div>
          <strong>Titolo originale: </strong> {{movie.original_title}}
        </div>
        <div>
          <strong>Voto: </strong> {{movie.vote_average}}
        </div>
        <div>
          <div v-if="flags.includes(movie.original_language)">
            <img class="language-img" 
            :src=" 
                require(`../assets/${movie.original_language}.png`)
                 "
            :alt="movie.original_language">
          </div>
          <div v-else><strong>Lingua: </strong> {{movie.original_language}}</div>
        </div>
        <div class="mb-5">
          <img v-if="movie.poster_path != null"
          :src="'https://image.tmdb.org/t/p/' + 'w342/' + movie.poster_path" 
          :alt="movie.title + 'poster'">
          <img v-else src="../assets/nope-not-here.webp" alt="image not found">
        </div>
      </div>
    </div>
    
    
    <h5 class="text-secondary">TV Shows:</h5>
    <div v-for="serie in series" :key="serie.id">
      <div class="mb-4">
        <div>
          <strong>Titolo: </strong> {{serie.name}}
        </div>
        <div>
          <strong>Titolo originale: </strong> {{serie.original_name}}
        </div>
        <div>
          <strong>Voto: </strong> {{serie.vote_average}}
        </div>
        <div>
          <div v-if="flags.includes(serie.original_language)">
            <img class="language-img"
            :src="
                  require(`../assets/${serie.original_language}.png`)
                 " 
            :alt="serie.original_language">
          </div>
          <div v-else><strong>Lingua: </strong> {{serie.original_language}}</div>
        </div>
        <div class="mb-5">
          <img v-if="serie.poster_path != null"
            :src="'https://image.tmdb.org/t/p/' + 'w342/' + serie.poster_path" 
            :alt="serie.name + 'poster'">
            <img v-else src="../assets/nope-not-here.webp" alt="image not found">
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
    },
    data(){
      return {
        flags: ['en', 'it', 'es', 'de', 'ja', 'fr'],
        
      }
    }
    
}
</script>

<style lang="scss" scoped>
.language-img{
  width: 30px;
  margin: 8px 0 10px 5px;
}
</style>