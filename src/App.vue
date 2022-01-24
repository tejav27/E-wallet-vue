<template>
  <div id="app">
    <Home @changeView="currentView='addcard'" v-if="currentView=='home'" :sendNewCard="sendToList"/>
    <AddCard @changeView="currentView='home'" v-if="currentView=='addcard'" @listNewCard="getData"/>
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
    sendToList:{}
  }},
  methods:{
    getData(retrievedInfo){
      this.sendToList={...retrievedInfo}
    }
  },
  updated(){
    this.sendToList
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
</style>
