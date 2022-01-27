<template>
  <div>
      <h3>ACTIVE CARD</h3>
    <Card  v-if="showActiveCard" :cardInfo="showActiveCard" />
    <Card v-else :cardInfo="firstcard"/>
    <button @click="deleteCard">Delete Card</button>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
    data(){return{
        showActiveCard:{...this.activeCardDetails}
    }},
  components: { Card },
  props: ["activeCardDetails", "firstCard"],
  watch: {
      activeCardDetails(){
          this.showActiveCard = this.activeCardDetails;
      }
  },
  mounted(){
    this.showActiveCard = this.firstCard
  },
  methods:{
      deleteCard(){
          this.$emit('deleteCard',{...this.showActiveCard})
          this.showActiveCard = this.firstCard
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
button{
    margin-top: -15px;
}
</style>