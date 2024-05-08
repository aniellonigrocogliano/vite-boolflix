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
       <h2>Titolo: {{movie.original_title}} </h2>
       <h2>Titolo originale: {{movie.original_title}} </h2>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>