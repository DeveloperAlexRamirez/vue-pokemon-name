<template>
  <div class="options-container">
    <h1 style="options-title">Pokemon Options</h1>
    <ul>
      <li
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        @click="$emit('selection')"
      >
        {{ pokemon.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    pokemons: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}
li {
  background-color: white;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  cursor: pointer;
  margin-bottom: 10px;
  min-width: 150px;
}

li:hover {
  background-color: rgba(0, 0, 0, 0.05);
}

.options-container {
  margin-top: 7rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.options-title {
  margin: 0px;
  font-size: 0.5rem;
}

@media screen and (min-width: 468px) {
  .options-container {
    margin-top: 13rem;
  }

  li {
    min-width: 250px;
  }

  .options-title {
    font-size: 2rem;
  }
}
</style>
