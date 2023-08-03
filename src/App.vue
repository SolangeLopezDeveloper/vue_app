<template>
  <div id="nav">
   <router-link to="/">Inicio</router-link>
  </div>
  <router-view></router-view>

</template>

<script>
export default {
  name: 'App'
}
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.category_container {
  border: 1px solid rgb(58, 45, 116);
  padding: 50px;
}
.searchInput{
  border: none;
  border-bottom: 1px solid rgb(58, 45, 116);
  min-height: 20px;
margin-top: 20px;
margin-bottom: 20px;
}
*{
  font-family: Georgia, 'Times New Roman', Times, serif;
}
</style>
