<template>

<header class="d-flex justify-content-between align-items-center">
    <!-- left-side -->
    <section class="left-header d-flex align-items-center">
        <!-- logo -->
        <div>
            <img class="logo" src="https://fontmeme.com/permalink/211201/0a43aa36584f2895324a0006b42b5d1a.png" alt="">
        </div>

        <!-- menù -->
        <ul class=" headerMenu ls-style d-flex">
            <li>Home</li>
            <li><a class="alist" href="#SerieTVclick">Serie Tv</a> </li>
            <li><a class="alist" href="#Filmclick">Film</a></li>
            <li>Nuovi e popolari</li>
            <li>La mia lista</li>
            
        </ul>
    </section>

    <!-- right-side -->
    <section class="right-header d-flex align-items-center">
        <!-- input text -->
        <form action="">
           <input 
             class="inRicerca"
             type="text" 
             placeholder="Cerca film e serie TV" 
             v-model.trim="searchMovie"
             @keyup.enter="$emit('perfSearch', searchMovie)"
            >
        <button @click.prevent="$emit('perfSearch', searchMovie)">Search</button>
        </form>

        <!-- icons -->
        <ul class="header-icons ls-style d-flex align-items-center" >
            <li><i class="fas fa-bell"></i></li>
            <li><img class="profileimg" src="@/assets/profilephoto.png" alt=""></li>
        </ul>
    </section>
    
</header>
  
</template>

<script>
export default {
    name: 'Header', 

    data() {
        return {
            searchMovie: '',
        }
    },

}
</script>

<style scoped lang="scss">
@import '@/components/variables.scss';


header {
    width: 100vw;
    background-color: rgba($color: #0a0a0a, $alpha: 0.8);
    padding: 10px;
    position: fixed;
    z-index: 1;
    

    .left-header{

        .logo{
            width: 100px;
            margin-left: 20px;
         }

         .headerMenu{
             font-size: 13px;
             color: rgb(231, 228, 228);
             margin-left: 30px;
             cursor: pointer;

             li {
                 margin: 10px;
                 transition: color 0.4s
             }
             li:hover{
                 color: $hovergray;
             }
         }
         
    }

    .right-header{
        .inRicerca,
        button {
           font-size: 12px;
           color: white;
           padding: 5px;
           margin-left: 10px;
           border: 1px solid white;
           background-color: transparent;
        }
        .inRicerca:focus {
            outline: none;
        }
        button:focus {
            color: $hovergray;
            border: 1px solid $hovergray;
        }
        

        .header-icons{
            color: white;
            margin-left: 30px;

            li {
                font-size: 20px;
                margin-right: 20px;
                cursor: pointer;
            }
        }

        .profileimg{
            width: 30px;
        }

    }

}


</style>