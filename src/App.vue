<template>
  <div id="app">
    <Home
      @changeView="currentView = 'addcard'"
      v-if="currentView == 'home'"
      :listOfCards="listOfCards"
      @deleteCard="deleteCard"
    />
    <AddCard
      @changeView="currentView = 'home'"
      v-if="currentView == 'addcard'"
      @listNewCard="getData"
    />
    <p v-if="showError">Same Card Number..</p>
  </div>
</template>

<script>
import Home from "./views/Home.vue";
import AddCard from "./views/AddCard.vue";
export default {
  name: "App",
  components: { Home, AddCard },
  data() {
    return {
      listOfCards: [
         {
          vendor: "bitcoin",
          cardColor: "#FFAE34",
          cardIcon: "bitcoin.svg",
          cardNumber: "3456 7891 5467 3425",
          name: "Kimberly Park",
          validMonth: 12,
          validYear: 24,
        },
      ],
      currentView: "home",
      matchedCard: 0,
      showError: false,
      index:null
    };
  },
  methods: {
    // getData(retrievedInfo){
    // this.matchedCard = this.listOfCards.filter(card => card.cardNumber == this.retrievedInfo.cardNumber)
    // console.log(this.matchedCard)
    // if(this.matchedCard==0){
    //   this.listOfCards.push({...retrievedInfo})
    //   this.showError=false
    // }
    // else{
    //   this.showError=true
    // }
    // },
    deleteCard(cardDetails){
      this.matchedCard = this.listOfCards.find(card => card.cardNumber == cardDetails.cardNumber)
       this.index=this.listOfCards.indexOf(this.matchedCard)
        this.listOfCards.splice(this.index,1)
    },
    getData(retrievedInfo) {
      this.listOfCards.push({ ...retrievedInfo });
    },
  },
  updated() {},
  created() {
    if (!localStorage.getItem("e-cards")) {
      localStorage.setItem("e-cards", JSON.stringify(this.listOfCards));
    } else {
      this.listOfCards = JSON.parse(localStorage.getItem("e-cards"));
    }
  },
  watch: {
    listOfCards: function () {
      localStorage.setItem("e-cards", JSON.stringify(this.listOfCards));
    },
  },
};
</script>

<style lang="scss">
#app {
  text-align: center;
  border: 2px solid rgb(117, 112, 112);
  border-radius: 6px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.6) ;
}
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap");
* {
  font-family: "Roboto", sans-serif;
}
button {
  border: black solid 2px;
  border-radius: 5px;
  background-color: white;
  color: black;
  font-size: 1rem;
  font-weight: bolder;
  padding: 15px 5px;
  margin-bottom: 30px;
}
button:hover {
  color: black;
  background-color: cadetblue;
}
</style>
