<template>
  <div v-if="pokemon">
    <div>#{{ pokemon.id }} - Name: {{ pokemon.name }} - Height: {{ pokemon.height }}</div>
    <b>Types:</b>
    <div v-for="(types, index) in pokemon.types" :key="index">
      <div v-for="(type, index) in types" :key="index">
        {{type.name}}
      </div>
    </div>
    ------------<br>
    <b>Abilities:</b>
    <div v-for="(moves, index) in pokemon.moves" :key="index">
      <div v-for="(move, index) in moves" :key="index">
        {{move.name}}
      </div>
    </div>
  </div>
</template>

<script>
import pokemon from '~/queries/pokemon'

export default {
  apollo: {
    pokemon: {
      query: pokemon,
      prefetch: ({ route }) => ({ id: route.params.id }),
      variables () {
        return { id: this.$route.params.id }
      }
    }
  },
  mounted() {
    console.log(this.$route.params.id)
  }
}
</script>
