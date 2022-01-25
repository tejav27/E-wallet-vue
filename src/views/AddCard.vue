<template>
  <div>
      <h1>Add Card</h1>
      <Card :updateCardData="this.retrievedInfo" />
      <InputForm @sendUpdate="retrieveData"/>
      <button @click="$emit('changeView'); $emit('listNewCard',{...retrievedInfo}); validateAndSend(retrievedInfo)">ADD CARD</button>
  </div>
</template>

<script>
import InputForm from '../components/InputForm.vue'
import Card from '../components/Card.vue'
export default {
  data(){return{
    retrievedInfo:{}
  }},
components:{Card, InputForm},
methods:{
  retrieveData(cardInfo){
    this.retrievedInfo= {...cardInfo};
  },
  validateAndSend(retrievedInfo){
    retrievedInfo.cardNumber
    if(retrievedInfo.cardNumber.toString().length != 16){
      console.log("errorrr should contain 16 digits")
    }
  }
},
}
</script>

<style scoped>
div{
  display: flex;
  flex-direction: column;
  place-items: center;
}
</style>