<template>
  <div>
    <div class="single-card" :style='{backgroundColor : cardInfo.cardColor}'>
      <section class="icons">
        <img v-bind:src="cardInfo.cardIcon" alt="icon">
        <div>
          <img :src="wifiIcon" alt="wifi" />
          <img :src="chipIcon" alt="chip" />
        </div>
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
        vendor: "vndr",
        cardNumber: "XXXX XXXX XXXX XXXX",
        name: "Firstname Lastname",
        validMonth: 11,
        validYear: 22,
      },
        wifiIcon: require("../assets/wifi.svg"),
        chipIcon: require("../assets/chip.svg"),
    };
  },
  props: ["updateCardData"],
  watch: {
    updateCardData() {
      this.cardInfo = { ...this.updateCardData };
    },
  },
};
</script>

<style scoped>
.single-card {
  text-align: center;
  margin: auto;
  margin-bottom: 50px;
  width: 350px;
  border: solid gray 2px;
  border-radius: 5px;
}
.icons {
  margin: 10%;
  display: flex;
}
.details {
  display: flex;
  justify-content: space-around;
}
</style>