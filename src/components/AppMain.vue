<script >

import axios from 'axios';
import { store } from '../store';
export default {

     data() {
          return {
               store
          }
     },
     methods: {
          bandiera(index) {
               return "https://countryflagsapi.com/png/"+store.movies[index].lang
               }
          }

     
};

</script>

<template>
     <h2>movie</h2>
     <div v-for="movie, index in store.movies" class="card">
          <h5>{{ movie.nome }}</h5>
          <p>{{ movie.lang }}</p>
          <p>{{ movie.voto }}</p>
          <img :src=bandiera(index) alt="">
     </div>
     <h2>serie</h2>
     <div v-for="serie, index in store.series" class="card">
          <h5>{{ serie.nome }}</h5>
          <p>{{ serie.nome_org }}</p>
          <p>{{ serie.voto }}</p>

     </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as*;

h1 {
     color: red;
     padding: 30px;
}

.ricerca {
     position: absolute;
     right: 50px;
     top: 50px;

     * {
          padding: 5px;
          margin: 10px;
     }
}

.card {
     padding: 20px;
}
</style>
