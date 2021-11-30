<template>

<header>
    <form action="">
        <input 
          type="text" 
          placeholder="Cerca film e serie TV" 
          v-model.trim="searchMovie"
          @keyup.enter="$emit('perfSearch', searchMovie)"
        >
        <button @click.prevent="$emit('perfSearch', searchMovie)">Search</button>
    </form>
</header>
  
</template>

<script>
export default {
    name: 'Header', 

    data() {
        return {
            searchMovie: '',
        }
    }

}
</script>

<style scoped lang="scss">
header {
    padding: 20px;
    display: flex;

    button {
        margin: 10px;
    }
}


</style>