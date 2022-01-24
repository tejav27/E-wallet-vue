<template>
  <div>
      <h3>ACTIVE CARD</h3>
    <Card v-if="activeCardDetails!=null" :retrieveActiveCard="activeCardDetails" />
    <Card v-else :retrieveActiveCard="firstCard" />
    <button @click="deleteCard">Delete Card</button>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: { Card },
  props: ["activeCardDetails", 'firstCard'],
  updated() {
    this.activeCardDetails;
  },
  methods:{
      deleteCard(){
          this.$emit('deleteCard',{...this.activeCardDetails})
      }
  }
};
</script>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  place-items: center;
  margin-bottom: 20px;
}
</style>