<template>
  <div class="p-3">
    <h5 class="text-secondary">Movies: </h5>
    <div v-for="movie in movies" :key="movie.id">
      <div class="mb-4">
        <div>
          <strong>Titolo: </strong> {{movie.title}}
        </div>
        <div>
          <strong>Titolo originale: </strong> {{movie.original_title}}
        </div>
        <div>
          <!-- 
          star-size= dimensione stelle; 
          :read-only= click sulle stelle per modificarle se è false(default);
          :rating= cosa votare (math.floor per arrotondare in negativo);
          :show-rating= su impostato su true stampa il numero delle stelle visualizzate;
          -->
          <star-rating :star-size="20" :read-only="true" :rating="Math.floor((movie.vote_average)/2)" :show-rating="false"/>
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
          <star-rating :star-size="20" :read-only=true :rating="Math.round((serie.vote_average)/2)" :show-rating="false"/>
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
import StarRating from 'vue-star-rating'

export default {
    name: 'Main',
    components:{
      StarRating
    },
    props:{
      movies: Array,
      series: Array,
      searchText: String,
    },
    data(){
      return {
        flags: ['en', 'it', 'es', 'de', 'ja', 'fr']
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