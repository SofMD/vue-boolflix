<template>
  <section>
      <ul>
          <li v-for="(el, index) in movies" :key="`movie-${index}}`">
              <cardMovie
                   :title="el.title"
                   :originalTitle="el.original_title"
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
    },

    

}
</script>

<style scoped lang="scss">

ul {
    margin: 30px;

    li{
        margin: 30px;
    }
}

</style>