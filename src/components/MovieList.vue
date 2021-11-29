<template>
  <section>
      <ul>
          <li v-for="(el, index) in movieList" :key="`movie-${index}}`">
              <h2>{{el.title}}</h2>
              <div>ORIGINAL TITLE: {{el.original_title}} </div>
              <div>LANGUAGE: {{el.original_language}} </div>
              <div>VOTE: {{el.vote_average}}</div>
          </li>
      </ul>
  </section>
</template>

<script>
import axios from 'axios'

export default {
    name: 'MovieList',

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