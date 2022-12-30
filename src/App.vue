<template>
  <!-- <b-container>
    <b-row>
      <b-col>
        <img 
          alt="Pokemon logo" src="../public/Logo-equipo-azul.png"
          height="200" width="200"
        />
      </b-col>
      <pokeCard class="col-lg-3"
        v-for="pokemon in arrayDatos" :key="pokemon"
        :name="pokemon.name" :url="pokemon.url"
      />
    </b-row>
  </b-container> -->

  <div class="container">
    <div class="row p-2">
        <div class="col-lg-12 mb-2">
          <img 
            alt="Pokemon logo"
            src="https://upload.wikimedia.org/wikipedia/commons/9/98/International_Pok%C3%A9mon_logo.svg"
          />
        <pokeCard class="col-lg-3"
          v-for="pokemon in arrayDatos"
          :key="pokemon"
          :name="pokemon.name"
          :url="pokemon.url"
        />
        </div>
    </div>
</div>
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
    this.capitalizeFirstLetter(this.arrayDatos);
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
    },
    capitalizeFirstLetter(arr) {
      arr.forEach(element => {
        const word = element.name
        const firstLetter = word.charAt(0).toUpperCase()
        const remainingLetter = word.slice(1)
        element.name = firstLetter + remainingLetter
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
