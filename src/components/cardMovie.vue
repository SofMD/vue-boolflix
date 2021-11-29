<template>
  <div>
        <h2>{{title}}</h2>
        <div>ORIGINAL TITLE: {{originalTitle}} </div>
        <div v-for="(ele, i) in flags" :key="`flag-${i}`">LANGUAGE: {{ele.en}} </div>
        <div>VOTE: {{vote}}</div>
        <!-- language -->
  </div>
</template>

<script>
export default {
    name: 'cardMovie',

    data(){
        return {
            flags: {
                it: '@/assets/it.png',
                en: '@/assets/en.png', 
            }
        };
     },

    props:{
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
    }

}
</script>

<style>

</style>