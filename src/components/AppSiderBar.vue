<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
  computed: {
    openClass() {
      return this.store.sidebarOpen ? 'offcanvas.show' : 'offcanvas';
    },

  },
  methods: {
    getImageFlag(imageName) {
      return new URL(`../assets/img/flag/${imageName}`, import.meta.url).href;
    },
    close() {
      this.store.sidebarOpen = false;
      this.store.idMovieTv = "";
    },
  },
};
</script>

<template>
  <div :class="openClass" class=" my-width offcanvas-end z-2 position-fixed bg-info-subtle " tabindex="2"
    id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
    <div class="offcanvas-header d-flex flex-nowrap justify-content-around">
      <h5 class="offcanvas-title" id="offcanvasRightLabel">Cast</h5>
      <button @click="close" type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body">
      <div class="row d-flex flex-nowrap justify-content-cente" v-for="cast in store.movieTvCast.slice(0, 5)">
        <div v-if="cast.profile_path" class="col m-3"><img class="poster"
            :src="`https://image.tmdb.org/t/p/w342${cast.profile_path}`" :alt="cast.name" /></div>
        <div v-else class="col m-3"><img class="poster" src="../assets/img/user-nopic.png" :alt="cast.name" /></div>
        <div class="col m-3">{{ cast.name }}</div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
img {
  border-radius: 50%;
  height: 50px;
  width: 50px;
}

.my-width {
  width: 25vw;
}

::-webkit-scrollbar {
  height: 7px;
  width: 7px;
}
</style>