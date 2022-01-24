<template>
  <div>
    <div class="single-card" :style="{ backgroundColor: cardInfo.cardColor }">
      <section class="icons">
        <div class="two-icons">
          <img :src="wifiIcon" alt="wifi" />
          <img :src="chipIcon" alt="chip" />
        </div>
        <img v-if="cardIconImg" :src="cardIconImage" alt="icon" />
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
        validYear: 22        
      },
      cardIconImg: null,
      wifiIcon: require("../assets/wifi.svg"),
      chipIcon: require("../assets/chip.svg"),
    };
  },
  props: ["updateCardData", "showCard", "retrieveActiveCard"],
  watch: {
    updateCardData() {
      this.cardInfo = { ...this.updateCardData };
      this.cardIconImg = this.updateCardData.cardIcon;
    },
    retrieveActiveCard() {
      this.cardInfo = { ...this.retrieveActiveCard };
      this.cardIconImg = this.retrieveActiveCard.cardIcon;
    },
  },
  mounted() {
    if (this.showCard) {
      this.cardInfo = { ...this.showCard };
      this.cardIconImg = this.showCard.cardIcon;
    }
  },
  computed: {
    cardIconImage() {
      if(this.cardIconImg) {
        return require("../assets/" + this.cardInfo.cardIcon);
      }
      return ''
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
}
.single-card {
  color: whitesmoke;
  text-align: center;
  margin-bottom: 2rem;
  width: 20rem;
  height: 15rem;
  border: solid gray 2px;
  border-radius: 1rem;
  box-shadow: 2px 2px 2px rgba(0,0,0,0.4) inset;
}
.icons {
  margin: 7%;
  display: flex;
  justify-content: space-between;
}
.two-icons {
  display: flex;
  flex-direction: column;
}
.details {
  margin-top: 10px;
  display: flex;
  justify-content: space-around;
}
</style>