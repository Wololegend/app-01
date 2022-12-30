<template>
  <img alt="Pokemon logo" src="../public/Logo-equipo-azul.png">
  <pokeCard
    v-for="pokemon in arrayDatos" :key="pokemon"
    :name="pokemon.name" :url="pokemon.url"
  />
</template>

<script>
import pokeCard from './components/pokeCard.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    pokeCard
  },
  data() {
    return {
      arrayDatos: []
    }
  },
  created() {
    this.getPokemon();
  },
  methods: {
    getPokemon() {
      var config = {
          method: 'get',
          url: 'https://pokeapi.co/api/v2/pokemon',
          headers: { }
        };

        axios(config)
        .then((response) => {
         this.arrayDatos = response.data.results
         console.log(this.arrayDatos)
        })
        .catch((e) => {
          console.log(e);
        });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
