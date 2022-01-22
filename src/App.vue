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
  margin-top: 60px;
}
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
*{
    font-family: 'Roboto', sans-serif;
}
</style>
