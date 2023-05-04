<template>
  <div class="header-top">
    <img src="../assets/img/logo-boolflix.png" alt="Boolflix Logo" />
  </div>
  <header class="app-header">
    <h4>Watch your favourite Show!</h4>
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

.header-top img {
  /* Personalizza le dimensioni del logo */
  width: 150px;
  height: auto;
}
</style>




