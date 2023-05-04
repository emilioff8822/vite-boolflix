<template>
  <div class="card-wrapper">
    <div class="card">
      <img :src="posterUrl" alt="Copertina" />
      <h3>{{ card.title || card.name }}</h3>
      <p>Titolo originale film: {{ card.original_title || card.original_name }}</p>
      <p>Lingua: {{ card.original_language }}</p>
      <p>Voto: {{ card.vote_average }}/10</p>
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
.card {
  width: 100%;
  text-align: center;
  margin-bottom: 20px;
  border: 1px solid black;
  background-color: black;
  color: white;
}
</style>
