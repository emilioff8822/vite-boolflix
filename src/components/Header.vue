<template>
  <div class="header-top">
   Boolflix
  </div>
  <header class="app-header">
    <h1>boolflix</h1>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.app-header {
  display: flex;
  justify-content: space-between;
  background-color: #333;
  color: white;
  padding: 1rem;
  margin-bottom: 40px;
}

.header-top {
  background-color: white;
  height: 80px;
  display: flex;
  align-items: center;
  padding-left: 20px;
  font-size: 24px;
  font-weight: bold;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
</style>
