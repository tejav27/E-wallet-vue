<template>
  <div>
    <h1>Add Card</h1>
    <Card :cardInfo="this.retrievedInfo" />
    <InputForm @sendUpdate="retrieveData" />
    <ul class="errors" v-if="showError">
      <li v-for="error in errorsList" :key="error">{{error}}</li>
    </ul>
    <button
      @click="
        validateAndSend(retrievedInfo);
      "
    >
      ADD CARD
    </button>
  </div>
</template>

<script>
import InputForm from "../components/InputForm.vue";
import Card from "../components/Card.vue";
export default {
  data() {
    return {
      retrievedInfo: {
        cardColor: "#3D3D3D",
        cardNumber: "XXXXXXXXXXXXXXXX",
        name: "CARDHOLDER NAME",
        validMonth: "MM",
        validYear: "YY",
      },
      noError:true,
      matchedCard:{},
      errorsList:[],
      showError:false
    };
  },
  props:['listOfCards'],
  components: { Card, InputForm },
  methods: {
    retrieveData(cardInfo) {
      this.retrievedInfo = { ...cardInfo };
    },
    validateAndSend(retrievedInfo) {
      this.errorsList = [];
      this.noError = true;
      this.showError = false;
      retrievedInfo.cardNumber;
      if (retrievedInfo.cardNumber.toString().length != 16) {
        this.errorsList.push("Card number should contain 16 digits");
        this.noError = false
      }
      if(!/^[a-zA-Z]+$/.test(retrievedInfo.name)){
        this.errorsList.push("Name should contain only characters")
        this.noError = false
      }
      this.matchedCard = this.listOfCards.find((card) => card.cardNumber == this.retrievedInfo.cardNumber)
      if(this.matchedCard){
        this.errorsList.push("The card number you have entered already exists")
        this.noError = false
      }
      if(retrievedInfo.cardNumber==""||retrievedInfo.name==""||retrievedInfo.validMonth==""||retrievedInfo.validYear==""||retrievedInfo.vendor==""){
        this.noError = false
        this.errorsList.push("Kindly fill in all the fields")
      }
      if(this.noError == true){
        this.$emit('changeView');
        this.$emit('listNewCard', { ...retrievedInfo });
      }
      else{
        this.showError = true
      }
    },
  },
};
</script>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  place-items: center;
}
.errors{
  color:red;
  font-weight: bolder;
  list-style:square;
  margin-top: -15px;
  text-align: left;
}
</style>