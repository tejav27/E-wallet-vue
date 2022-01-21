<template>
  <div>
      <h1>Cardlist</h1>
      <AddCard v-if="listNewCard"/>
  </div>
</template>

<script>
import AddCard from '../views/AddCard.vue'
export default {
  components:{AddCard}
}
</script>

<style>

</style>