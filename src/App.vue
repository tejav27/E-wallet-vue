<template>
  <div id="app">
    <Home @changeView="currentView='addcard'" v-if="currentView=='home'"  :listOfCards="listOfCards"/>
    <AddCard @changeView="currentView='home'" v-if="currentView=='addcard'" @listNewCard="getData"/>
    <p v-if="showError">Same Card Number..</p>
  </div>
</template>

<script>
import Home from './views/Home.vue'
import AddCard from './views/AddCard.vue'
export default {
  name: 'App',
  components:{Home, AddCard},
  data(){return{
    listOfCards:[
      {
          vendor: "bitcoin",
          cardColor: "red",
          cardIcon: null,
          cardNumber: "5768906789",
          name: "fghjklghjk",
          validMonth: 11,
          validYear: 22,
        },
        {
          vendor: "evilcorp",
          cardColor: "yellow",
          cardIcon: null,
          cardNumber: "3456789",
          name: "xfcgvjhbnkml",
          validMonth: 12,
          validYear: 3456,
        },
        {
          vendor: "ninja",
          cardColor: "green",
          cardIcon: null,
          cardNumber: "122345678934567",
          name: "dfguhijopkedrtfgyuhjif",
          validMonth: 2,
          validYear: 3332,
        },
    ],
    currentView:"home",
    matchedCard:0,
    showError:false
  }},
  methods:{
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

    getData(retrievedInfo){
      this.listOfCards.push({...retrievedInfo})
    }


},
  updated(){
  },
   mounted(){
          if(!localStorage.getItem('e-cards')){
            localStorage.setItem('e-cards',JSON.stringify(this.listOfCards))
          }
          else{
            this.listOfCards=JSON.parse(localStorage.getItem('e-cards'))
          }

  },
  watch: {
  listOfCards: function () {
      localStorage.setItem('e-cards', JSON.stringify(this.listOfCards))
  }
}
  
}
</script>

<style lang="scss">
#app {
  text-align: center;
}
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
*{
    font-family: 'Roboto', sans-serif;
}
button{
  border: darkcyan;
  border-radius: 5px;
  background-color: cadetblue;
  color: #000;
  padding: 15px 5px;
}
button:focus{
  color: black;
  background-color: cadetblue;
}
</style>
