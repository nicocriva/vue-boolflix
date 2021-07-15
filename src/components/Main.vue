<template>
  <div class="p-3">
    <div class="show-card">
      <h5 class="text-secondary py-3">Movies: </h5>
      <div class="d-flex prova-flex">
        <div v-for="movie in movies" :key="movie.id">
          <div class="mb-4 mx-2">
            <div class="show-container mb-5 position-relative">
              <img v-if="movie.poster_path != null"
              :src="'https://image.tmdb.org/t/p/' + 'w342/' + movie.poster_path" 
              :alt="movie.title + 'poster'">
              <img class="not-found-img" v-else src="../assets/not-found.jpeg" alt="image not found">
              <div class="shadow text-light position-absolute w-100 h-100">
                <div class="show-info h-100 overflow-auto p-3">
                  <div v-if="movie.title != movie.original_title">
                    <div>
                      <h5>{{movie.title}}</h5>
                    </div>
                    <div>
                      <strong>Titolo originale: </strong> {{movie.original_title}}
                    </div>
                  </div>
                  <div v-else>
                    <h5>{{movie.title}}</h5>
                  </div>
                  <div v-if="movie.overview != ''">
                    <strong>Trama: </strong> <span>{{movie.overview}}</span>
                  </div>
                  <div>
                    <!-- star-size= dimensione stelle; 
                    :read-only= click sulle stelle per modificarle se è false(default);
                    :rating= cosa votare (math.floor per arrotondare in negativo);
                    :show-rating= su impostato su true stampa il numero delle stelle visualizzate; -->
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
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="show-card">
      <h5 class="text-secondary py-3">Series: </h5>
      <div class="d-flex prova-flex">
        <div v-for="serie in series" :key="serie.id">
          <div class="mb-4">
            <div class="show-container mb-5 mx-2  position-relative">
              <img v-if="serie.poster_path != null"
              :src="'https://image.tmdb.org/t/p/' + 'w342/' + serie.poster_path" 
              :alt="serie.title + 'poster'">
              <img v-else src="../assets/not-found.jpeg" alt="image not found">
              <div class="shadow text-light position-absolute w-100 h-100">
                <div class="show-info p-3">
                  <div v-if="serie.name != serie.original_name">
                    <div>
                      <h5>{{serie.name}}</h5>
                    </div>
                    <div>
                      <strong>Titolo originale: </strong> {{serie.original_name}}
                    </div>
                  </div>
                  <div v-else>
                    <h5>{{serie.name}}</h5>
                  </div>
                  <div v-if="serie.overview != ''">
                    <strong>Trama: </strong> <span>{{serie.overview}}</span>
                  </div>
                  <div>
                    <star-rating :star-size="20" :read-only="true" :rating="Math.floor((serie.vote_average)/2)" :show-rating="false"/>
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
                </div>
              </div>
            </div>
          </div>
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
.show-card{
  width: 342px;
  margin-top: 40px;

  .prova-flex{
    width: 97vw;
    flex-wrap: wrap;
  }

  .show-container{

    &:hover .shadow{
      display: block;
    }

    .not-found-img{
      height: 513px;
    }

    .shadow{
      background-color: rgba(8, 4, 4, 0.8);
      display: none;
      top: 0;
      left: 0;
    }
}
}


.language-img{
  width: 30px;
  margin: 8px 0 10px 5px;
}
</style>