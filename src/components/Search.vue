<template>
  <div class="search-container">
    <input type="text" v-model="searchText" placeholder="Cerca" class="search-input" />
    <select v-model="selectedType" class="search-select">
      <option value="all">All</option>
      <option value="movie">Film</option>
      <option value="tv">Serie TV</option>
    </select>
    <button @click="emitSearch" class="search-btn">Search</button>
    <button @click="reset" class="search-btn">Reset</button>
  </div>
</template>


<script>
export default {
  name: "Search",
  data() {
    return {
      searchText: "",
      selectedType: "",
    };
  },
  methods: {
    emitSearch() {
      this.$emit("search-input", this.searchText);
      this.$emit("type-selected", this.selectedType);
    },
    reset() {
      this.searchText = "";
      this.selectedType = "";
      this.emitSearch();
      this.$emit("reset-search");
    },
  },
};
</script>
<style lang="scss" scoped>

.search-container {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 20px;
}

.search-input,
.search-select,
.search-btn {
  border-radius: 25px;
  font-size: 18px;
  padding: 8px 16px;
}

.search-btn {
  background-color: #383a38;
  color: white;
  border: none;
  cursor: pointer;
  transition: 0.3s;

  &:hover {
    background-color: #1e874b;
  }
}

</style>
