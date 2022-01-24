<template>
  <div>
      <h3>ACTIVE CARD</h3>
    <Card :retrieveActiveCard="activeCardDetails" />

  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: { Card },
  props: ["activeCardDetails"],
  updated() {
    this.activeCardDetails;
  },
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