<template>
<div>
    <h1>Team</h1>
    <PokemonList :pokemons="team" :teamMode="true" />
</div>
</template>

<script>
import PokemonList from "../components/PokemonList.vue"
export default {
    name: 'Team',
    components: {
        PokemonList
    },
    data() {
        return {
        }
    },
    computed: {
        team() {
        return this.$root.$data.team;
        }
    },
    methods: {
    }
}
</script>