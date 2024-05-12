<script>
import { store } from "../store";
import axios from "axios";
export default {
  props: {
    cardObj: Object,
  },
  data() {
    return {
      store,

    };
  },
  computed: {

    title() {
      return this.cardObj.title ? this.cardObj.title : this.cardObj.name;

    },
    originalTitle() {
      return this.cardObj.original_title ? this.cardObj.original_title : this.cardObj.original_name;
    }
  },
  methods: {
    getImageFlag(imageName) {

      return new URL(`../assets/img/flag/${imageName}.png`, import.meta.url).href;

    },
    getImageStar(imageName) {
      imageName = Math.round(imageName);
      return new URL(`../assets/img/star/${imageName}.png`, import.meta.url).href;
    },
    openMovie() {
      this.store.sidebarOpen = true;
      this.store.idMovieTv = this.cardObj.id;
      let linkCast = "https://api.themoviedb.org/3/movie/" + this.store.idMovieTv + "/credits";

      const paramsObj = {
        api_key: this.store.keyId,
        language: "it-IT",
      };
      axios
        .get(linkCast, {
          params: paramsObj,
        })
        .then((resp) => {
          this.store.movieTvCast = resp.data.cast;
        });

    },
    openTv() {
      this.store.sidebarOpen = true;
      this.store.idMovieTv = this.cardObj.id;
      let linkCast = "https://api.themoviedb.org/3/tv/" + this.store.idMovieTv + "/credits";

      const paramsObj = {
        api_key: this.store.keyId,
        language: "it-IT",
      };
      axios
        .get(linkCast, {
          params: paramsObj,
        })
        .then((resp) => {
          this.store.movieTvCast = resp.data.cast;
        });

    },
  },

};
</script>

<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img v-if="cardObj.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342${cardObj.poster_path}`"
          :alt="cardObj.title" />
        <img v-else class="poster" src="../assets/img/no-poster.jpg" :alt="cardObj.title" />
      </div>
      <div class="flip-card-back">
        <p>Titolo: {{ title }} </p>
        <p v-if="title !== originalTitle">Titolo originale: {{ originalTitle }} </p>
        <p>Lingua: <img :src="getImageFlag(cardObj.original_language)" :alt="cardObj.original_language" /> </p>
        <p>Voto: <img :src="getImageStar(cardObj.vote_average)" :alt="cardObj.vote_averagee" /> </p>
        <p> Trama: {{ cardObj.overview }} </p>
        <button v-if="cardObj.title" @click="openMovie" type="button" class="btn btn-info btn-sm"
          data-bs-target="#offcanvasRight">Cast</button>
        <button v-else @click="openTv" type="button" class="btn btn-info btn-sm"
          data-bs-target="#offcanvasRight">Cast</button>

      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.poster {
  width: 100%;
}

.flip-card {
  background-color: transparent;
  width: 325px;
  height: 550px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #434343;
  color: black;
}

.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
}

p {
  font-size: 0.8rem;
}
</style>