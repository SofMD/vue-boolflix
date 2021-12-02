<template>
  <div id="app">

    <Header @perfSearch="getMovie" />

    <!-- main -->
    <main>
      <MovieList :movies="movieList" :serietv="serieTvList" />
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
            serieTvList: null,
            searchText: '',
        };
     },

    created() {
      this.firstlist()
       

    },

    methods: {

      // serie e film dati dalla ricerca input
        getMovie(text){
          this.searchText = text;

            //prendo dati da API
            axios.get('https://api.themoviedb.org/3/search/movie',{
                params: {
                    api_key: '3035d057024a2a14b3c4646d0b7ba466',
                    query: text ,
                    language: 'it-IT'
                }
            })
            .then(result => {
                this.movieList = result.data.results;
            })
            .catch(err => console.log(err));


            //serie tv 
            axios.get('https://api.themoviedb.org/3/search/tv', {
              params: {
                    api_key: '3035d057024a2a14b3c4646d0b7ba466',
                    query: text ,
                    language: 'it-IT'
                }
            })
            .then(result => {
                this.serieTvList = result.data.results;
            })
            .catch(err => console.log(err));
        },

        // serie e film presenti dall'inizio
        firstlist(){
         if(this.movieList === null || this.serieTvList === null){
           axios.get('https://api.themoviedb.org/3/search/movie',{
                params: {
                    api_key: '3035d057024a2a14b3c4646d0b7ba466',
                    query: 'i' ,
                    language: 'it-IT'
                }
              })
              .then(result => {
                this.movieList = result.data.results;
              })
              .catch(err => console.log(err));

          }

          axios.get('https://api.themoviedb.org/3/search/tv', {
              params: {
                    api_key: '3035d057024a2a14b3c4646d0b7ba466',
                    query: 'i' ,
                    language: 'it-IT'
                }
            })
            .then(result => {
                this.serieTvList = result.data.results;
            })
            .catch(err => console.log(err));
        
        }
    },
}

</script>

<style lang="scss">
@import '@/components/utilitys.scss';


*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}


body {
   background-color: #141414;
}

</style>
