<template>
  <div>
      <h1>Home</h1>
      <CardList :sendNew="sendNewCard"/>
      <button @click="$emit('changeView')">ADD A NEW CARD</button>
  </div>
</template>

<script>
import CardList from '../components/CardList.vue'
export default {
  props:['sendNewCard'],
  components:{CardList},
  updated(){
    this.sendNewCard
  }
}
</script>

<style>

</style>