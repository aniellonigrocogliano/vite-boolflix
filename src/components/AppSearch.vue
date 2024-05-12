<script>
import { store } from "../store";
import axios from "axios";
export default {
  data() {
    return {
      store,
      itemSearch: "",
    };
  },
  methods: {
    getSearch() {
      this.store.itemSearch = this.itemSearch;
      const paramsObj = {
        api_key: this.store.keyId,
        query: this.store.itemSearch,
        language: "it-IT",
      };
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: paramsObj,
        })
        .then((resp) => {
          this.store.movieArray = resp.data.results;
        });

      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: paramsObj,
        })
        .then((resp) => {
          this.store.tvArray = resp.data.results;

        });
    },
  },
};

</script>

<template>
  <header>
    <div class="container d-flex header flex-nowrap">
      <div class="p-3"> <img src="../assets/img/logo.png" alt="logo" /></div>
      <div class="input-group mb-3 p-3">
        <input v-model="itemSearch" type="text" class="form-control" placeholder="" aria-label="Recipient's username"
          aria-describedby="button-addon2">
        <button @click="getSearch()" class="btn btn-outline-secondary" type="button" id="button-addon2">Cerca</button>
      </div>

    </div>
  </header>
</template>
<style scoped>
header {
  height: 100px;
  background-color: black;
}

img {
  width: 25%;
}
</style>