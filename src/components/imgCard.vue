<template>
    <img :src="img"/>
</template>

<script>
import axios from 'axios'

export default {
    name: 'imgCard',
    props: ['url'],
    data () {
       return {
            img: String
        }
    },
    created(){
      this.getPokemonImage(this.url);
    },
    methods: {
        getPokemonImage(url) {
          var config = {
              method: 'get',
              url: url,
              headers: { }
            };

            axios(config)
            .then((response) => {
             this.img = response.data.sprites.front_default
             console.log(this.img)
            })
            .catch((e) => {
              console.log(e);
            });
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
</style>