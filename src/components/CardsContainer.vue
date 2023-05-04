<template>
  <div class="pg-card-container">
    <Card v-for="card in store.resultArray" :key="card.id" :card="card"/>
  </div>
</template>

<script>
import {store} from '../data/store';
import Card from './partials/Card.vue';
export default {
  name: 'CardsContainer',  
  components: {
    Card  
  },
  data() {
    return{
      store
    }  
  }
}
</script>

<style lang="scss" scoped>
.pg-card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px; 
  justify-content: center; 
}

.card-wrapper {
  width: calc(20% - 20px); 
  margin-bottom: 20px; 
}
</style>
