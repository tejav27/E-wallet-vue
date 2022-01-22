<template>
  <div class="list-style">
    <Card class="list-item"
      v-for="listItem in list"
      :key="listItem.vendor"
      :showCard="{ ...listItem }"
    />
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
    props:['sendNew'],
  components: { Card },
  data() {
    return {
      list: [
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
    };
  },
  updated(){
      this.list
      this.sendNew
      console.log(this.sendNew)
      console.log(this.list)
      localStorage.setItem('e-cards', JSON.stringify(this.list))
  },
  mounted(){
      if(this.sendNew.cardNumber){
          this.list.push({...this.sendNew})
      }
          // if(!localStorage.getItem('e-cards')){
          //   localStorage.setItem('e-cards',JSON.stringify(this.list))
          // }
          // else{
          //   this.list=JSON.parse(localStorage.getItem('e-cards'))
          // }

  },
};
</script>

<style scoped>
/* .list-style{
    position: absolute;
} */
/* .list-item{
    position: relative;
    transform: translateY(-20%);
} */
</style>