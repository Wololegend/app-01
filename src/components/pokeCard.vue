<template>
<div class="pokeCard">

    <ul>
      <li v-for="item in arrayDatos" :key="item">
        <a :href="item.url"> {{item.name}} </a>
    </li>
    </ul>

</div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'pokeCard',
    props: ['msg'],
    data () {
       return {
            arrayDatos: [],
            arrayImgs: []
        }
    },
    created(){
      this.getArrayImgs();
    },
    methods: {
        getList() {
          var config = {
              method: 'get',
              url: 'https://pokeapi.co/api/v2/pokemon/',
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
        getImgs(id) {
          var config = {
              method: 'get',
              url: 'https://pokeapi.co/api/v2/pokemon/' + id + '/sprites/front_default',
              headers: {}
            };

            axios(config)
            .then((response) => {
             this.arrayDatos.push(response.data)
            })
            .catch((e) => {
              console.log(e);
            });
        },
        getArrayImgs() {
          for (let i = 1; i <= 20; i++) {
            this.getImgs(i.toString());
          }

          console.log(this.arrayImgs)
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>