<script setup>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';
</script>

<template>
  <div class="categoryStyle">
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
  <p>Sol López</p>

<hr/>

<div v-for="category in categories" :key="category.idCategory">
  <img v-bind:src="category.strCategoryThumb" alt="">
  <h6>{{ category.strCategory }}</h6>
  <p>{{ category.strCategoryDescription }}</p>

</div>

</template>

<script>
export default {
  name: 'App',
data(){
  return {
    categories: []
  }
},

mounted(){
  axios.get('https://themealdb.com/api/json/v1/1/categories.php')
  .then((response) =>{
console.log(response.data.categories);
//idCategory,strCategory,strCategoryDescription, strCategoryThumb
this.categories = response.data.categories
  })
  .catch((error)=>{console.log(error);})
}
}</script>

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
.categoryStyle{
  border: 1px solid red;
  padding: 50px;
}
</style>
