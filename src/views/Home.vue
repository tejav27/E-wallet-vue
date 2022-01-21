<template>
  <div>
      <h1>Home</h1>
      <CardList/>
      <button @click="$emit('changeView')">ADD A NEW CARD</button>
  </div>
</template>

<script>
import CardList from '../components/CardList.vue'
export default {
  components:{CardList}
}
</script>

<style>

</style>