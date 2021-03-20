<template>
<div class="wrapper">
  <div class="pokemons">
    <div class="pokemon" v-for="(pokemon,index) in pokemons" :key="pokemon.id">
        <div class="info" :style="{ 'background-color': getColor(pokemon.type) }">
            <h1>{{pokemon.name}} {{pokemon.id}}</h1>
            <h2>{{pokemon.type}}</h2>
        </div>
        <div class="image">
            <img :src="'/images/'+pokemon.image">
        </div>
        <div class="moves" :style="{ 'background-color': getColor(pokemon.type) }">
            <h2> 1. {{pokemon.move1}}</h2>
            <h2> 2. {{pokemon.move2}}</h2>
        </div>
        <div class="button">
            <button class="auto" v-if="teamMode === false" @click="addToTeam(pokemon)">Add to Team</button>
            <button class="auto" v-else @click="removeFromTeam(index)">Remove</button>
        </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
    name: 'PokemonList',
    props: {
        pokemons: Array,
        teamMode: Boolean
    },
    methods: {
        addToTeam: function(pokemon) {
          this.$root.$data.team.push(pokemon);
        },
        removeFromTeam(index) {
          this.$root.$data.team.splice(index, 1);
        },
        getColor(type) {
          switch(type) {
              case "Grass":
                return "#C6FFB4";
              case "Fire":
                return "#FFC36F";
              case "Water":
                return "#6FD6FF";
              case "Poison":
                return "#BB8BFF";
              case "Bug":
                return "#DDFFA6";
              case "Flying":
                return "#A6FFF5";
              case "Normal":
                return "#BEBEBE";
              default:
                return "black";
            }
        }
    }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.pokemons {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.pokemon {
  border: 2px solid #333;
  border-radius: 5px;
  margin: 10px;
  margin-top: 30px;
  width: 300px;
}

.pokemon img {
  height: 250px;
  width: 300px;
  object-fit: cover;
}

.pokemon .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #b3ffc7;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}

.moves {
  background: #b3ffc7;
  color: black;
}

.moves h2 {
    padding: 10px;
    margin: 0px;
}

button {
  height: 50px;
  width: 300px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>