<template>
  <div class="container">
    <div class="container-pokemones">
      <img :src="imgSrc" class="hidden-pokemon" alt="pokemon" />

      <img v-if="showPokemon" :src="imgSrc" class="fade-in" alt="pokemon" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pokemonId: {
      type: Number,
    },

    showPokemon: {
      type: Boolean,
      required: true,
      default: false,
    },
  },

  computed: {
    imgSrc() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
    },
  },
};
</script>

<style scoped>
img {
  max-height: 100px;
  position: absolute;
  user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  -webkit-user-drag: none;
  -webkit-user-select: none;
}
.hidden-pokemon {
  filter: brightness(0);
}

@media screen and (min-width: 468px) {
  img {
    max-height: 200px;
  }
}

.container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.container-pokemones {
  display: flex;
  justify-content: center;
}
</style>
