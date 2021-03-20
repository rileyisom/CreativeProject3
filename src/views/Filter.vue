<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select('Grass')" href="#" class="pure-menu-link">Grass</a></li>
      <li class="pure-menu-item"><a @click="select('Fire')" href="#" class="pure-menu-link">Fire</a></li>
      <li class="pure-menu-item"><a @click="select('Water')" href="#" class="pure-menu-link">Water</a></li>
      <li class="pure-menu-item"><a @click="select('Poison')" href="#" class="pure-menu-link">Poison</a></li>
      <li class="pure-menu-item"><a @click="select('Bug')" href="#" class="pure-menu-link">Bug</a></li>
      <li class="pure-menu-item"><a @click="select('Flying')" href="#" class="pure-menu-link">Flying</a></li>
      <li class="pure-menu-item"><a @click="select('Normal')" href="#" class="pure-menu-link">Normal</a></li>
    </ul>
  </div>
  <PokemonList :pokemons="pokemons" />
</div>
</template>

<script>
import PokemonList from "../components/PokemonList.vue"
export default {
  name: 'Filter',
  components: {
    PokemonList
  },
  data() {
    return {
      type: '',
    }
  },
  computed: {
    pokemons() {
      return this.$root.$data.pokemons.filter(pokemon => pokemon.type === this.type);
    }
  },
  methods: {
    select(type) {
      this.type = type;
    }
  }
}
</script>