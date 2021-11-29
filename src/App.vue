<template>
  <div id="app">

    <Header @perfSearch="searchMovie" />

    <!-- main -->
    <main>
      <MovieList :movies="movieList"/>
    </main>

  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import MovieList from '@/components/MovieList.vue';


export default {
  name: 'App',
  components: {
    Header,
    MovieList,
  },

    data(){
        return {
            movieList: null,
            searchText: '',
        };
     },

    computed: {
      movieFilter(){
        return this.movieList.filter(item => {
          return item.title.toLowerCase().includes(this.searchText.toLowerCase())
        })
        
      },
    },


    created(){
        this.getMovie();
    },

    methods: {
        searchMovie(text) {
          console.log(text);
          this.searchText = text;
        },

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
        },
    },
}

</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}
</style>
