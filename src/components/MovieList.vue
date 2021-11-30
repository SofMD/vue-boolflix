<template>
  <section>
      <!-- lista film -->
      <ul>
          <li v-for="(el, index) in movies" :key="`movie-${index}`">
              <cardMovie
                   :poster="`https://image.tmdb.org/t/p/w185/${el.poster_path}`"
                   :title="el.title"
                   :originalTitle="el.original_title"
                   :language="el.original_language"
                   :vote="el.vote_average"
                />
          </li>
      </ul>

      <!-- lista serie tv -->
      <ul>
          <li v-for="(el, index) in serietv" :key="`SERIE-${index}`">
              <cardMovie
                   :poster="`https://image.tmdb.org/t/p/w185/${el.poster_path}`"
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
section{
    display: flex;
    justify-content: space-around;
}

ul {
    margin: 30px;

    li{
        margin: 30px;
    }
}

</style>