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
               axios.get('https://api.themoviedb.org/3/search/movie?api_key=b14cb6542ceb213de135cbf06fce03e7&query=' + store.ricerca).then((response) => {
                    console.log(response.data.results)
                    let response_movie = response.data.results;
                    response_movie.forEach(element => {

                         let obj = {
                              nome: element.original_title,
                              image: element.poster_path,
                              lang: element.original_language,
                              voto: element.vote_average

                         }

                         this.store.movies.push(obj)
                    });
                    console.log(this.store.movies)

               })
               store.movies=[],
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
