<template>
  <div class="card">
    <imgCard :url="url"></imgCard>
    <div class="card-body">
      <h5 class="card-title"> {{name}} </h5>
    </div>
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