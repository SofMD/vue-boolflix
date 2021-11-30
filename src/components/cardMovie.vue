<template>
  <div class="card">
        <h2>{{ title }}</h2>
        <div>ORIGINAL TITLE: {{ originalTitle }} </div>
        <div > 
          LANGUAGE:
          <img 
            v-if="isFlag"
            :src="require(`../assets/${ language }.png`)"
          >
          <span v-else>{{ language }}</span>
        </div>
         <div>VOTE: {{ vote }}</div>

  </div>
</template>

<script>
export default {
    name: 'cardMovie',

    data(){
        return {
            flags: ['it', 'en']
        };
    },

    computed: {
      isFlag(){
        return this.flags.includes(this.language);
      }
    },

    props:{
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
    }

}
</script>

<style scoped lang="scss">
.card {

  img{
    width: 30px;
  }
}

</style>