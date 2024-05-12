<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";
export default {
  components: {
    AppCard,
  },
  data() {
    return {
      store,
    };
  },
  methods: {

  },
};
</script>

<template>

  <body>
    <div class="container">
      <section>
        <h1>Film</h1>
        <div class="row row-cols-4">
          <div class="col" v-for="movie in store.movieArray">
            <AppCard :cardObj="movie" />
          </div>
        </div>
      </section>
      <section>
        <h1>Serie Tv</h1>
        <div class="row row-cols-4">
          <div class="col" v-for="tv in store.tvArray">
            <AppCard :cardObj="tv" />
          </div>
        </div>
      </section>
    </div>
  </body>
</template>

<style lang="scss" scoped>
body {
  background-color: #434343;
}
</style>