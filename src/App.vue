<template>
  <div id="app" class="page-wrapper">
    <div class="container">
      <Header />
      <Search @search-input="updateSearch" @type-selected="updateType" @reset-search="resetSearch" />
      <CardsContainer />
      <Footer />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { store } from "./data/store";
import Header from "./components/Header.vue";
import Search from "./components/Search.vue";
import CardsContainer from "./components/CardsContainer.vue";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Header,
    Search,
    CardsContainer,
    Footer,
  },
  methods: {
    getApi(searchText = "", type = "all") {
    const apiKey = "189665c00565925740541aecbd96aade";

    // controllo per verificare se sia searchText che type sono vuoti
    if (searchText === "" && type === "all") {
      
      // Se entrambi sono vuoti, carico la pagina di default con popular
      let url = `https://api.themoviedb.org/3/movie/popular?api_key=${apiKey}&language=it-IT&page=1`;

      axios.get(url).then((result) => {
        store.resultArray = result.data.results;
      });
    } else {
      // Altrimenti, eseguo la ricerca come prima
      let url = `https://api.themoviedb.org/3/search/multi?api_key=${apiKey}&query=${searchText}&language=it-IT`;

      if (type !== "all") {
        if (type === "movie") {
          url = url.replace("multi", "movie");
        } else if (type === "tv") {
          url = url.replace("multi", "tv");
        }
      }

      axios.get(url).then((result) => {
        store.resultArray = result.data.results;
      });
    }
    },
    updateSearch(searchText) {
      this.currentSearch = searchText;
      this.getApi(searchText, this.currentType);
    },
    updateType(selectedType) {
    this.currentType = selectedType;
    this.getApi(this.currentSearch, selectedType);
  },
    resetSearch() {
      this.currentSearch = "";
      this.currentType = "all";
      this.getApi(this.currentSearch, this.currentType);
    },
  },
  data() {
    return {
      currentSearch: "",
      currentType: "all",
    };
  },
  mounted() {
    this.getApi();
  },
};
</script>


<style lang="scss">
@import "bootstrap/scss/bootstrap.scss";

.page-wrapper {
  background-color:black;
  padding: 90px 90px;
  box-sizing: border-box;
  min-height: 100vh;
  position: relative;
}

.container {
  background-color: black;
  padding: 0;
  box-sizing: border-box;
  min-height: 100%;
  position: relative;
  top: -90px;
}

body {
  margin: 0;
}
</style>
