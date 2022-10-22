<script setup>
  import { ref } from 'vue';
  import PokemonCard from "../components/pokemon/ui/Card.vue"
  
  let pokemons = ref("888")

  async function func1(){
    const data = await fetch('https://pokeapi.co/api/v2/pokemon');

    pokemons.value = await data.json();
  }

 func1()

</script>

<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div v-for="pokemon of pokemons.results" 
      :key="pokemon.name">

      <PokemonCard :pokemon="pokemon" />
      
    </div>
  </div>
</template>


<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
