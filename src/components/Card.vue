<template>
  <div>
    <div class="single-card" :style="{ backgroundColor: cardInfo.cardColor }">
      <section class="icons">
        <div class="two-icons">
          <img src="../assets/wifi.svg" alt="wifi" />
          <img src="../assets/chip.svg" alt="chip" />
        </div>
        <img :src="cardIconImage" alt="" />
      </section>
      <h3>{{ formattedCardNumber }}</h3>
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
  props: ["cardInfo"],
  computed: {
    cardIconImage() {
      if (this.cardInfo.vendor) {
        return require("../assets/" + this.cardInfo.vendor + ".svg");
      }
      return "";
    },
    formattedCardNumber() {
      if (this.cardInfo.cardNumber) {
        let x = this.cardInfo.cardNumber.toString();
        let c1 = x.substring(0,4), c2 = x.substring(4,8), c3 = x.substring(8,12), c4 = x.substring(12,16) ;
        return c1 + " " + c2 + " " + c3 + " " + c4;
      }
      return "xxxx xxxx xxxx xxxx";
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
  background-color: #3D3D3D;
  text-align: center;
  margin-bottom: 2rem;
  width: 20rem  ;
  height: 15rem;
  border: solid gray 2px;
  border-radius: 1rem;
  box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.4) inset;
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