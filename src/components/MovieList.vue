<template>
  <section>
      <ul>
          <li v-for="(el, index) in movieList" :key="`movie-${index}}`">
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
import axios from 'axios';
import cardMovie from '@/components/cardMovie.vue'

export default {
    name: 'MovieList',

    components: {
        cardMovie,
    },

    data(){
        return {
            movieList: [],
        };
    },
    created(){
        this.getMovie();
    },
    methods: {
        getMovie(){
            //prendo dati da API

            axios.get('https://api.themoviedb.org/3/search/movie',{
                params: {
                    api_key: '3035d057024a2a14b3c4646d0b7ba466',
                    query: 'marvel' ,
                    language: 'it-IT'
                }
            })
            .then(result => {
                console.log(result.data.results)
                this.movieList = result.data.results;
            })
            .catch(err => console.log(err));
        }
    }

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