<template>
  <h1 v-if="!pokemon">Espere por favor...</h1>
  <!-- Picture -->
  <div v-else class="container">
    <h1>¿Quién es este Pokemón?</h1>
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon" />

    <!-- Opciones -->
    <PokemonOptions :pokemons="pokemonArr" />
  </div>
</template>

<script>
import PokemonPicture from '@/components/PokemonPicture';
import PokemonOptions from '@/components/PokemonOptions';
import getPokemonOptions from '@/helpers/getPokemonOptions.js';

export default {
  components: {
    PokemonPicture,
    PokemonOptions,
  },

  data() {
    return {
      pokemonArr: [],
      pokemon: null,
      showPokemon: false,
    };
  },

  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions();

      const rndInt = Math.floor(Math.random() * 4);
      this.pokemon = this.pokemonArr[rndInt];
    },
  },

  // Hooks lifecycle
  mounted() {
    this.mixPokemonArray();
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
