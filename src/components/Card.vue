<template>
  <div>
    <div class="single-card" :style="{ backgroundColor: cardInfo.cardColor }">
      <section class="icons">
        <div class="two-icons">
          <img :src="wifiIcon" alt="wifi" />
          <img :src="chipIcon" alt="chip" />
        </div>
        <img v-bind:src="cardInfo.cardIcon" alt="icon" />
      </section>
      <h3>{{ cardInfo.cardNumber }}</h3>
      <section class="details">
        <div>
          <h5>CARDHOLDER NAME</h5>
          <h3>{{ cardInfo.name }}</h3>
        </div>
        <div>
          <h5>VALID UNTILL</h5>
          <h3>{{ cardInfo.validMonth }}/{{ cardInfo.validYear }}</h3>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cardInfo: {
        cardNumber: "XXXX XXXX XXXX XXXX",
        name: "Firstname Lastname",
        validMonth: 11,
        validYear: 22,
      },
      wifiIcon: require("../assets/wifi.svg"),
      chipIcon: require("../assets/chip.svg"),
    };
  },
  props: ["updateCardData", "showCard"],
  watch: {
    updateCardData() {
      this.cardInfo = { ...this.updateCardData };
    },
  },
  mounted() {
    if(this.showCard){
      this.cardInfo = { ...this.showCard };
    }
  },
};
</script>

<style scoped>
*{
  box-sizing: border-box;
}
.single-card {
  text-align: center;
  margin: auto;
  margin-bottom: 50px;
  width: 450px;
  height: 300px;
  border: solid gray 2px;
  border-radius: 10px;
  box-shadow: black 2px;
}
.icons {
  margin: 7%;
  display: flex;
  justify-content: space-between;
}
.two-icons{
  display: flex;
  flex-direction: column;
}
.details {
  display: flex;
  justify-content: space-around;
}
</style>