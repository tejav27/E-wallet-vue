<template>
  <div>
      <h1>Home</h1>
      <CardList :listOfCards="listOfCards"/>
      <button @click="$emit('changeView')">ADD A NEW CARD</button>
  </div>
</template>

<script>
import CardList from '../components/CardList.vue'
export default {
  props:['listOfCards'],
  components:{CardList},
  updated(){
  }
}
</script>

<style>

</style>