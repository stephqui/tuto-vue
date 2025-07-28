<template>
<p>Compteur : {{ count }}</p>
<button v-on:click="count++">Incrémenter</button>
<button @click="decrement">Décrémenter</button>
</template>

<script setup>
import {ref} from 'vue'

const count = ref(0)
const increment =(event)=>{
  count.value++
}
const decrement =()=>{
  count.value--
}
</script>