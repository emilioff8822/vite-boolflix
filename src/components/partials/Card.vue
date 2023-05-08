<template>
  <div class="card-wrapper">
    <div class="card">
      <img v-if="posterUrl" :src="posterUrl" alt="Copertina" />
      <img v-else src="../../assets/img/nondisp.jpg" alt="Immagine non disponibile" />
      <div class="card-info">
        <h3>{{ card.title || card.name }}</h3>
        <p>Titolo originale film: {{ card.original_title || card.original_name }}</p>
        <p>Lingua: {{ card.original_language }}</p>
        <div class="rating"> Voto:
          <font-awesome-icon v-for="n in getStars" :key="n" icon="star"  class="star" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core';
import { faStar } from '@fortawesome/free-solid-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

library.add(faStar);

export default {
  name: "Card",
  props: {
    card: {
      type: Object,
      required: true,
    },
  },
  computed: {
    posterUrl() {
      if (this.card.poster_path) {
        const baseUrl = "https://image.tmdb.org/t/p/";
        const imageSize = "w342";
        return baseUrl + imageSize + this.card.poster_path;
      } else {
        return null;
      }
    },
    getStars() {
      return Math.ceil(this.card.vote_average / 2);
    },
  },
  components: {
    FontAwesomeIcon,
  },
};
</script>



<style lang="scss" scoped>
.card-wrapper {
  width: calc(20% - 20px);
  margin-bottom: 20px;
  position: relative;
}

.card {
  background-color: rgba(255, 255, 255, 0.8);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  overflow: hidden;
  position: relative;
}

.card img {
  width: 100%;
  display: block;
}

.card:hover {
  background-color: rgba(17, 17, 17, 0.6);
}

.card-info {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(100, 100, 100, 0.8);
  color: white;
  padding: 10px;
  display: flex;
  flex-direction:column;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: opacity 0.6s;
}

.card:hover .card-info {
  opacity: 1.0;
}

.rating {
  display: flex;
  justify-content: center;
  gap: 2px;
  margin-top: 10px;
}

.star {
  color: gold;
}
</style>

