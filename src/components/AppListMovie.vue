<script>
import { store } from "../store";

export default {
  components: {
  },
  data() {
    return {
      store,
    };
  },
  
};
</script>

<template>
  <div class="container">
    
    <div class="row row-cols-4">
      <div class="col" v-for="movie in store.movieArray">
       <p>Titolo: {{movie.title}} </p>
       <p>Titolo originale: {{movie.original_title}} </p>
       <p>Lingua: {{movie.original_language}} </p>
       <p>Voto: {{movie.vote_average}} </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>