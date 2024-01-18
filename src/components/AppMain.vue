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
               return "https://flagcdn.com/16x12/" + store.movies[index].lang + ".png"
          },

          stelle_m(index){
              return  Math.ceil(store.movies[index].voto /2)
          },
          stelle_s(index){
              return  Math.ceil(store.series[index].voto /2)
          }
     }



};

</script>

<template>
     <h2>movie</h2>
     <div class="container">
          <div v-for="movie, index in store.movies" class="card">
               <img :src=movie.image alt="">
               <h5>{{ movie.nome }}</h5>
               <p>{{ movie.lang }}</p>
               <p>{{  stelle_m(index) }}</p>
               <img :src=bandiera(index) alt="">
          </div>
     </div>
     <h2>serie</h2>
     <div class="container">
          <div v-for="serie, index in store.series" class="card">
               <img :src=serie.image alt="">
               <h5>{{ serie.nome }}</h5>
               <p>{{ serie.nome_org }}</p>
               <p>{{  stelle_s(index) }}</p>
               <img :src=bandiera(index) alt="">
          </div>
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
