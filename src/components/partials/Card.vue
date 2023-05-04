<!-- Card.vue -->
<template>
  <div class="card-wrapper">
    <div class="card">
      <img :src="posterUrl" alt="Copertina" />
      <div class="card-info">
        <h3>{{ card.title || card.name }}</h3>
        <p>Titolo originale film: {{ card.original_title || card.original_name }}</p>
        <p>Lingua: {{ card.original_language }}</p>
        <p>Voto: {{ card.vote_average }}/10</p>
      </div>
    </div>
  </div>
</template>

<script>
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
      const baseUrl = "https://image.tmdb.org/t/p/";
      const imageSize = "w342";
      return baseUrl + imageSize + this.card.poster_path;
    },
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
  flex-direction: column;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: opacity 0.6s;
}

.card:hover .card-info {
  opacity: 1.0;
}

</style>
