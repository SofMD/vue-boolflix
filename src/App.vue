<template>
  <div id="app">

    <Header/>

    <!-- main -->
    <main>
      <MovieList/>
    </main>

  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import MovieList from '@/components/MovieList.vue';

export default {
  name: 'App',
  components: {
    Header,
    MovieList,

  }
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
