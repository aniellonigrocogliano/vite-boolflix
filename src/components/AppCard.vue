<script>

export default {
  props: {
    cardObj: Object,
  },
  computed: {

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
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
       <img class="poster" :src="`https://image.tmdb.org/t/p/w342${cardObj.poster_path}`" :alt="cardObj.title"/>
      </div>
      <div class="flip-card-back">
            <p>Titolo: {{cardObj.title}} </p>
          <p>Titolo originale: {{cardObj.original_title}} </p>    
          <p>Lingua: <img :src="getImageFlag(cardObj.original_language)" :alt="cardObj.original_language" /> </p>
          <p>Voto: <img :src="getImageStar(cardObj.vote_average)" :alt="cardObj.vote_averagee" /> </p>
          <p> Trama: {{cardObj.overview}} </p>
      </div>   
    </div>
  </div>
</template>

<style lang="scss" scoped>
.poster{
  width:100%;
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
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
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
</style>