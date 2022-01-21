<template>
  <div>
      <h1>Cardlist</h1>
      <!-- <AddCard v-if@listNewCard="createNewCard"/> -->
  </div>
</template>

<script>
// import AddCard from '../views/AddCard.vue'
export default {
  // components:{AddCard},
  methods: {
    createNewCard(retrievedInfo){
      console.log(retrievedInfo)
    }
  }
}
</script>

<style>

</style>