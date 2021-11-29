<template>
  <div>
        <h2>{{title}}</h2>
        <div>ORIGINAL TITLE: {{originalTitle}} </div>
        <div>LANGUAGE: {{language}} </div>
        <div>VOTE: {{vote}}</div>
  </div>
</template>

<script>
export default {
    name: 'cardMovie',

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