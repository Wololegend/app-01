<template>
  <div>
    <imgCard :url="url"></imgCard>
    <h5> {{name}} </h5>
  </div>
</template>

<script>
import imgCard from './imgCard.vue'

export default {
    name: 'pokeCard',
    props: ['url', 'name'],
    components: {
      imgCard
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
</style>