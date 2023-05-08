<script>
import {store} from "../data/store";
export default {
  name: "Footer",
  data(){
    return{
      store
    }
  }
}
</script>

<template>
  <h2 class="text-center my-5">Sono stati caricati {{ store.resultArray.length }} Risultati</h2>
</template>

<style>
h2 {
  color: rgb(162, 161, 161);
}
</style>
