<template>
  <p>Compteur : {{ count }}</p>
  <button v-on:click="count++">Incrémenter</button>
  <button @click="decrement">Décrémenter</button>
  <hr>
  <button @click="sortMovies">Réorganiser</button>
  <form action="" @submit="addMovie">
    <input type="text" placeholder="Nouveau film" v-model="movieName">
    <button>Ajouter film</button>
    {{ movieName }}
  </form>
  <ul>
    <li v-for="movie in movies" :key="movie">
      {{ movie }} <button @click="deleteMovie(movie)">Supprimer</button>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
const movieName = ref('')
const movies = ref([
  'Matrix',
  'Lilo & Stitch',
  'Titanic'
])

const increment = (event) => {
  count.value++
}
const decrement = () => {
  count.value--
}

const deleteMovie = (movie) => {
  movies.value = movies.value.filter(m => m != movie)
}

const sortMovies = () => {
  movies.value.sort((a, b) => a > b ? 1 : -1)
}

const addMovie = () => {
  movies.value.push(movieName.value)
  movieName.value = ''
}
</script>

main.js
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')