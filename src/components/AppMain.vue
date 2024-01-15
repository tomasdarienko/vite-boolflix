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


     }
};

</script>

<template>

<div v-for="movie, index in store.movies" class="card">
          <h5>{{ store.movies[index].nome }}</h5>
          <p>{{ store.movies[index].lang }}</p>
          <p>{{ this.store.movies[index].voto }}</p>
          
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
     .card{
          padding: 20px;
     }
</style>
