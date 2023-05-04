<template>
  <div class="card-wrapper">
    <div class="card">
      <h3>{{ card.title || card.name }}</h3>
      <p>Titolo originale: {{ card.original_title || card.original_name }}</p>
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
