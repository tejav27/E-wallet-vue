<template>
  <div class="home">
    <h1 class="heading">E-WALLET</h1>
    <ActiveCard :activeCardDetails="activeCardDetails" :listOfCards="listOfCards" @deleteCard="deleteCard"/>
    <CardList :listOfCards="listOfCards" @showActiveCard="activeCardInfo" />
    <button @click="$emit('changeView')">ADD A NEW CARD</button>
  </div>
</template>

<script>
import ActiveCard from "../components/ActiveCard.vue";
import CardList from "../components/CardList.vue";
export default {
  data() {
    return {
      activeCardDetails: {},
    };
  },
  props: ["listOfCards"],
  components: { CardList, ActiveCard },
  methods: {
    activeCardInfo(cardDetails) {
      this.activeCardDetails = { ...cardDetails };
    },
    deleteCard(cardDetails){
      this.$emit('deleteCard', {...cardDetails});
    }
  },
};
</script>

<style scoped>
.heading{
  font-weight:bolder;
}
</style>