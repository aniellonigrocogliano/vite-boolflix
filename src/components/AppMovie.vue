<script>
import { store } from "../store";
import axios from "axios";
export default {
  data() {
    return {
      store,
    };
  },
  created() {
    this.getMovie();
  },
  methods: {
    getMovie() {
      const paramsObj = {
        api_key:this.store.keyId,
        query:this.store.itemSearch,
        language:"it-IT",
      };
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: paramsObj,
        })
        .then((resp) => {
            console.log(resp);
            this.store.movieArray = resp.data.results;
            console.log(this.store.movieArray);
        });
    },
},
};

</script>

<template>
    <div class="container"> 
        
    </div>

</template>
<style scoped>

</style>