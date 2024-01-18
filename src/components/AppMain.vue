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

          stelle_m(index) {
               return Math.ceil(store.movies[index].voto / 2)
          },
          stelle_s(index) {
               return Math.ceil(store.series[index].voto / 2)
          }
     }



};

</script>

<template>
     <h2>Movie</h2>
     <div class="container">

          <div v-for="movie, index in store.movies" class="card flip-card">
               <div class="flip-card-inner">
                    <div class="flip-card-front">
                         <img :src=movie.image alt="">
                    </div>
                    <div class="flip-card-back">

                         <h5>Titolo:  {{ movie.nome }}</h5>
                         <h5></h5>
                         <p>Voto: {{ stelle_m(index) }}</p>
                         <p>Lingua originale: <img :src=bandiera(index) alt=""> </p>
                         <p>Trama:  {{ movie.overview }}</p>
                    </div>
               </div>
          </div>

     </div>
     <h2>Serie</h2>
     <div class="container">

          <div class="flip-card card" v-for="serie, index in store.series">
               <div class="flip-card-inner">
                    <div class="flip-card-front">
                         <img :src=serie.image alt="">
                    </div>
                    <div class="flip-card-back">

                         <h5>Titolo:  {{ serie.nome }}</h5>
                         <p>titolo originale: {{ serie.nome_org }}</p>
                         <p>Voto: {{ stelle_s(index) }}</p>
                         <p>Lingua originale: <img :src=bandiera(index) alt=""> </p>
                         <p>Trama:  {{ serie.overview }}</p>

                    </div>
               </div>
          </div>

     </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as*;

h1 {
     color: red;
     padding: 30px;
}
h2{
     font-size: 40px;
     border-bottom: 5px solid red;
     margin-bottom: 50px;
     padding-left: 50px;
     margin-top: 50px;
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
     // padding: 20px;
}



.flip-card {
  background-color: transparent;
  width: 300px;
  height: 450px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;

  img{
     max-width: 300px;
  }
}

.flip-card-back {
  background-color: #000000;
  color: white;
  transform: rotateY(180deg);
  border: 1px solid red;
  font-size: 20px;
  overflow-y: auto;
}
</style>
