<template>
  <div class="card">
        <img
          v-if="poster"
         :src="`https://image.tmdb.org/t/p/w185/${poster}`"
         :alt="title"
         >
         <img 
          class="nullposter"
          v-else
          :src="require('../assets/nullposter.png')" 
          :alt="title"
         >
        <h2>{{ title }}</h2>
        <div>ORIGINAL TITLE: {{ originalTitle }} </div>
        <div > 
          LANGUAGE:
          <img 
            class="langFlags"
            v-if="isFlag"
            :src="require(`../assets/${ language }.png`)"
          >
          <span v-else>{{ language }}</span>
        </div>
         <div>
           VOTE: 
            <span v-for="(n, index) in votestar()" :key="`vote-${index}`"> <i class="fas fa-star"></i></span>
    
          </div>

  </div>
</template>

<script>
export default {
    name: 'cardMovie',

    data(){
        return {
            flags: ['it', 'en'],
            newvote: Number,
        };
    },

    computed: {
      isFlag(){
        return this.flags.includes(this.language);
      }
    },

    props:{
        poster: String,
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
    },

    methods: {
      votestar(){
        this.newvote = Math.ceil(this.vote / 2);
        console.log(this.newvote)
        return this.newvote
      
      }
    }



}
</script>

<style scoped lang="scss">
.card {

  .langFlags{
    width: 30px;
  }

  .nullposter{
    width: 185px;
  }
}

</style>