<template>
  <div>
    <h1>Activecard</h1>
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