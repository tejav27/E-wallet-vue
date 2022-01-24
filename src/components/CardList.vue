<template>
  <div class="list-style">
    <Card class="list-item"
      v-for="listItem in listOfCards"
      :key="listItem.cardNumber"
      :showCard="{ ...listItem }"
      @click="cardclicked"
    />
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
    props:['listOfCards'],
  components: { Card },
  data() {
    return {
    };
  },
  // watch:{
  //   sendNew: function (){ 
  //     console.log(++this.count)
  //         console.log('helloooo')
  //         this.list.push({...this.sendNew})
  //   }
  // },
  updated(){
      // this.list
      // this.sendNew
      // console.log(this.sendNew)
      // console.log(this.list)
      // localStorage.setItem('e-cards', JSON.stringify(this.list))
  },
  mounted(){
      // // this.list=JSON.parse(localStorage.getItem('e-cards'))
          // if(!localStorage.getItem('e-cards')){
          //   localStorage.setItem('e-cards',JSON.stringify(this.list))
          // }
          // else{
          //   this.list=JSON.parse(localStorage.getItem('e-cards'))
          // }

  },
  methods:{
    cardclicked(){
      console.log('clikeddddd card')
    }
  }
};
</script>

<style lang="scss">
*{
  box-sizing: border-box;
}
@for $i from 1 through 8 {
  .list-item:nth-child(#{$i}n) {
    position: relative;
    z-index: calc($i + 4);
  }
}
.list-style{
  display: flex;
  flex-direction: column;
  place-items: center;
  margin-bottom: 20px;
}
.list-item:not(:first-child){
  margin-top: -15rem;
}
</style>