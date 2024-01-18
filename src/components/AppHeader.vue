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
          cerca_carta() {
               axios.get('https://api.themoviedb.org/3/search/movie?api_key=b14cb6542ceb213de135cbf06fce03e7&language=it_IT&query=' + store.ricerca).then((response) => {
                    // console.log(response.data.results)
                    let response_movie = response.data.results;
                    response_movie.forEach(element => {

                         let obj = {
                              nome: element.original_title,
                              image: "https://image.tmdb.org/t/p/w342/"+element.poster_path,
                              lang: element.original_language,
                              voto: element.vote_average,
                              overview: element.overview,

                         }

                         this.store.movies.push(obj)
                    });
                    // console.log(this.store.movies)

               })
               axios.get('https://api.themoviedb.org/3/search/tv?api_key=b14cb6542ceb213de135cbf06fce03e7&language=it_IT&query=' + store.ricerca).then((response) => {
                    console.log(response.data.results)
                    let response_series = response.data.results;
                    response_series.forEach(element => {

                         let obj = {
                              nome: element.name,
                              overview: element.overview,
                              nome_org: element.original_name,
                              image: "https://image.tmdb.org/t/p/w342/"+element.poster_path,
                              lang: element.original_language,
                              voto: element.vote_average

                         }

                         this.store.series.push(obj)
                    });
                    console.log(this.store.series)

               })
               store.movies=[],
               store.series=[],
               store.ricerca=''

          }
     }
};

</script>

<template>
     <h1>
          BoolFix
     </h1>

     <div class="ricerca">
          <button @click="cerca_carta()">cerca</button>
          <input type="text" v-model="store.ricerca">
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

     *{
          padding: 5px;
          margin: 10px;
     }
}
</style>
