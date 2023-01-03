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
  </b-container> ESTO SÓLO FUNCIONA CON BOOTSTRAP VUE INSTALADO-->

<!-- La página está dividida en una serie de rows y cols. No podemos controlar cuántos hay,
sólo cuántos rows/cols mide cada uno de nuestros elementos. La img de Pokemon mide 12 cols,
mientras que la PokeCard (cada una) sólo 3. -->
  <div class="container">
    <div class="row p-2">
        <div class="col-lg-12 mb-2">
          <img 
            alt="Pokemon logo"
            src="https://upload.wikimedia.org/wikipedia/commons/9/98/International_Pok%C3%A9mon_logo.svg"
          />
        </div>
        <pokeCard class="col-lg-3"
          v-for="pokemon in arrayDatos"
          :key="pokemon"
          :name="capitalizeFirstLetter(pokemon.name)"
          :url="pokemon.url"
        >
        </pokeCard>
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
    capitalizeFirstLetter(name) {
        const word = name
        const firstLetter = word.charAt(0).toUpperCase()
        const remainingLetter = word.slice(1)
        name = firstLetter + remainingLetter

        return name
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
