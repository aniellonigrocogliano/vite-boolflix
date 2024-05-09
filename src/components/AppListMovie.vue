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
  methods: {
    getImageFlag(imageName) {
      return new URL(`../assets/img/flag/${imageName}.png`, import.meta.url).href;
    },
    getImageStar(imageName) {
      imageName=Math.round(imageName);
      return new URL(`../assets/img/star/${imageName}.png`, import.meta.url).href;
    },
    
  },
};
</script>

<template>
  <div class="container">
    <div class="row row-cols-4">
      <div class="col" v-for="movie in store.movieArray">
       <p>Titolo: {{movie.title}} </p>
       <p>Titolo originale: {{movie.original_title}} </p>    
       <p>Lingua: <img :src="getImageFlag(movie.original_language)" :alt="movie.original_language" /> </p>
       <p>Voto: <img :src="getImageStar(movie.vote_average)" :alt="movie.vote_averagee" /> </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>