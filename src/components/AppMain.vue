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
          bandiera(code) {
               store.movies[index].lang.toUpperCase().replace(/./g, char => String.fromCodePoint(char.charCodeAt(0)+127397) );
               }
          }

     
};

</script>

<template>
     <h2>movie</h2>
     <div v-for="movie, index in store.movies" class="card">
          <h5>{{ store.movies[index].nome }}</h5>
          <p>{{ store.movies[index].lang }}</p>
          <p>{{ this.store.movies[index].voto }}</p>

     </div>
     <h2>serie</h2>
     <div v-for="serie, index in store.series" class="card">
          <h5>{{ store.series[index].nome }}</h5>
          <p>{{ store.series[index].nome_org }}</p>
          <p>{{ this.store.series[index].voto }}</p>

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
