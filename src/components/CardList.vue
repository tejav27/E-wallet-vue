<template>
  <div class="list-style">
    <Card class="list-item"
      @click.native="showActiveCard(listItem)"
      v-for="listItem in listOfCards"
      :key="listItem.cardNumber"
      :showCard="{ ...listItem }"
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
  methods:{
    showActiveCard(cardDetails){
      this.$emit('showActiveCard',{...cardDetails})
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