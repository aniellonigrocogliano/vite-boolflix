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
    <section>
      <h1>Film</h1>
    <div class="row row-cols-4">
      <div class="col" v-for="movie in store.movieArray">
       <p>Titolo: {{movie.title}} </p>
       <p>Titolo originale: {{movie.original_title}} </p>    
       <p>Lingua: <img :src="getImageFlag(movie.original_language)" :alt="movie.original_language" /> </p>
       <p>Voto: <img :src="getImageStar(movie.vote_average)" :alt="movie.vote_averagee" /> </p>
      </div>
    </div>
  </section>
  <section>
      <h1>Serie tv</h1>
    <div class="row row-cols-4">
      <div class="col" v-for="tv in store.tvArray">
       <p>Titolo: {{tv.name}} </p>
       <p>Titolo originale: {{tv.original_name}} </p>    
       <p>Lingua: <img :src="getImageFlag(tv.original_language)" :alt="tv.original_language" /> </p>
       <p>Voto: <img :src="getImageStar(tv.vote_average)" :alt="tv.vote_averagee" /> </p>
      </div>
    </div>
  </section>
  </div>
</template>

<style lang="scss" scoped></style>