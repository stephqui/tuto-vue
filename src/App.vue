<template>
  <p>Compteur : {{ count }}</p>
  <button v-on:click="count++">Incrémenter</button>
  <button @click="decrement">Décrémenter</button>
  <ul>
    <li v-for="movie in movies">
      {{ movie }} <button @click="deleteMovie(movie)">Supprimer</button>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
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
</script>