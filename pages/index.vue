<template>
  <div class="container">
    <div class="pokemon" v-for="(pokemon, key) in pokemonList" :key="key">
      {{pokemon.name}} - {{pokemon.url}}
    </div>
  </div>
</template>

<script>
import pokemonList from '~/queries/pokemon-list'

export default {
  apollo: {
    pokemonList: {
      prefetch: true,
      query: pokemonList
    }
  },
  mounted() {
    console.log(pokemonList)
  },
}
</script>

<style>
.pokemon {
  display: flex;
}
</style>
