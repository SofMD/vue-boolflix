<template>
  <section>
      <!-- lista film -->
      <h2>FILM</h2>
      <ul class="movieList ls-style d-flex fl-wrap">
          <li v-for="(el, index) in movies" :key="`movie-${index}`">
              <cardMovie
                   :poster="el.poster_path"
                   :title="el.title"
                   :originalTitle="el.original_title"
                   :language="el.original_language"
                   :overview="el.overview"
                   :vote="el.vote_average"
                />
          </li>
      </ul>

      <!-- lista serie tv -->
      <h2>SERIE TV</h2>
      <ul class="serieList ls-style d-flex fl-wrap">
          <li v-for="(el, index) in serietv" :key="`SERIE-${index}`">
              <cardMovie
                   :poster="el.poster_path"
                   :title="el.name"
                   :originalTitle="el.original_name"
                   :language="el.original_language"
                   :vote="el.vote_average"
                />
          </li>
      </ul>
  </section>
</template>

<script>
import cardMovie from '@/components/cardMovie.vue'

export default {
    name: 'MovieList',

    components: {
        cardMovie,
    },

    props: {
        movies: Array,
        serietv: Array,
    },

    

}
</script>

<style scoped lang="scss">
@import '@/components/variables.scss';

section{
    padding: 30px ;
    padding-top: 100px;

    h2{
        font-size: 25px;
        color: white;
        transition: color 0.4s
    }
    h2:hover{
        color: $hovergray;
    }
}

.movieList,
.serieList{
    justify-content: space-between;
    margin-top: 40px;
    margin-bottom: 40px;

    li{
        width: 225px;
        margin-bottom: 50px;
        margin-right: 10px;
    }
}


</style>