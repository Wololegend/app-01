<template>
  <div class="card" style="width: 18rem;">
    <imgCard :url="url"></imgCard>
    <div class="card-body">
      <h5 class="card-title"> {{name}} </h5>
    </div>
  </div>

  <!-- <div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div> -->
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