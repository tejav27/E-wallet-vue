<template>
  <div>
      <h3>ACTIVE CARD</h3>
    <Card v-if="listOfCards.length > 0" :cardInfo="showActiveCard" :class="{'fade' : deleteDialog==true}"/>
      <h4 v-else> Please add some cards </h4> 
    <button @click="deleteDialog=true" v-if="listOfCards.length > 0">Delete Card</button>
    <DeleteConfirmationDialog  v-if="deleteDialog" @confirmDeletion="deleteCard" @goBack="deleteDialog=false"/>
  </div>
</template>

<script>
import DeleteConfirmationDialog from "./DeleteConfirmationDialog.vue"
import Card from "./Card.vue";
export default {
    data(){return{
        showActiveCard:{...this.activeCardDetails},
        deleteDialog:false
    }},
  components: { Card, DeleteConfirmationDialog },
  props: ["activeCardDetails", "listOfCards"],
  watch: {
      activeCardDetails(){
          this.showActiveCard = {...this.activeCardDetails};
      }
  },
  mounted(){
    this.showActiveCard = this.listOfCards[0]
  },
  methods:{
      deleteCard(){
          this.$emit('deleteCard',{...this.showActiveCard})
          this.showActiveCard = {...this.listOfCards[0]}
          this.deleteDialog = false
      }
  }
};
</script>

<style scoped lang="scss">
div {
  display: flex;
  flex-direction: column;
  place-items: center;
  margin-bottom: 20px;
}
button{
    margin-top: -15px;
}
h4{
  margin-bottom: 45px;
}
.fade{
  opacity: 0.5;
}

</style>