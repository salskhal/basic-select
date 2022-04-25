<template>

  <h1>Hello world</h1>
  <form @submit.prevent="search">
  <input type="text" v-model="film" list="availableBreeds" />
  </form>
  <datalist id="availableBreeds">
    <option v-for="breed in availableBreeds" :key="breed.id">{{ breed.name }}</option>
  </datalist>
  <h1>{{film}}</h1>
</template>

<script setup>
import {ref, onMounted} from "vue"

const availableBreeds = ref([]);
const film = ref("")

const API_KEY = "7c306308-15a5-45c8-9f7f-d215f10ddf53";



onMounted(() => {
    fetch(`https://api.thecatapi.com/v1/breeds?api_key=${API_KEY}`)
    .then((res) => res.json())
    .then((breeds) => {
      console.log(breeds)
      availableBreeds.value = breeds
      
    });
})


const search = () =>{
  
} 

// const fetchBreads = () => {
//   fetch(`https://api.thecatapi.com/v1/breeds?api_key=${API_KEY}`)
//     .then((res) => res.json())
//     .then((breeds) => {
//       availableBreeds.value = breeds.map(breed => breed.name)
//     });
// };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
