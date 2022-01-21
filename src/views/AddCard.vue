<template>
  <div>
      <h1>Add Card</h1>
      <Card :updateCardData="this.retrievedInfo" />
      <InputForm @sendUpdate="retrieveData"/>
      <button @click="$emit('changeView'); $emit('listNewCard',{...retrievedInfo})">ADD CARD</button>
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
  }
},
}
</script>

<style>

</style>