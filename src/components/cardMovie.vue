<template>
  <div class="card">
    <!-- immagini -->
    <div class="cardPoster">
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
    </div>

    <div class="textCard ">
        <!-- titolo -->
        <div class="t-up card-title mb">  {{ title }}</div>
        
        <!-- titolo originale -->
        <div class="mb">{{ originalTitle }} </div>
        <!-- lingua -->

        <div class="mb"> 
          Language:
          <img 
            class="langFlags"
            v-if="isFlag"
            :src="require(`../assets/${ language }.png`)"
          >
          <span v-else>{{ language }}</span>
        </div>
        <!-- descrizione -->
        
         <div class="overview mb">{{overview}}</div>
         
        <!-- voto -->
         <div class="mb">
           Vote: 
            <span v-for="(n, index) in votestar()" :key="`vote-${index}`"> <i class="fas fa-star"></i></span>
          </div>
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
        overview: String,
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
  font-size: 12px;
  transition: all .2s;

  .cardPoster,
  .nullposter{
    width: 235px;

    img {
      width: 100%;
      height: 330px;
      object-fit: cover;
      object-position: top;
    }
  }

  .textCard{
    display: none;
    color: white;
    width: 100%;


    .langFlags{
        width: 20px;
    }

    .card-title{
      font-size: 14px;
      font-weight: bolder;
    }

    .overview{
      padding: 5px;
      font-size: 8px;
    }

  }


}

.card:hover {
  transform: scale(1.2);
  position: relative;
  
  .cardPoster{
    filter: opacity(30%);
  }

  .textCard{
    display: block;
    position: absolute;
    top: 15px;
    left: 7px;

  }
}

</style>