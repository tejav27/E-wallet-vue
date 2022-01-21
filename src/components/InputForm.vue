<template>
  <div>
    <form>
      <label for="input">CARD NUMBER</label>
      <input
        type="text"
        placeholder="Enter card number"
        v-model="cardInfo.cardNumber"
      />
      <label for="input">CARDHOLDER NAME</label>
      <input
        type="text"
        placeholder="Enter card name"
        v-model="cardInfo.name"
      />
      <label for="input">MONTH</label>
      <input
        type="number"
        placeholder="Month"
        v-model="cardInfo.validMonth"
        min="1"
        max="12"
      />
      <label for="input">YEAR</label>
      <input
        type="number"
        placeholder="Year"
        v-model="cardInfo.validYear"
        min="2022"
      />
      <label for="input">Vendor</label>
      <select v-model="cardInfo.vendor" v-on:change="assignColor($event); assignIcon($event)">
        <option v-for="vendor in Vendors" :key="vendor.bgColor" >
          {{ vendor.vName }}
        </option>
      </select>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cardInfo: {
        vendor: "",
        cardColor: "",
        cardIcon: null, 
        cardNumber: "",
        name: "",
        validMonth: null,
        validYear: null,
      },
      Vendors: [
        { bgColor: "#FFAE34", vName: "bitcoin", vIcon:"/img/bitcoin.68939348.svg" },
        { bgColor: "#8B58F9", vName: "blockChain", vIcon: "/img/blockchain.a26084d8.svg" },
        { bgColor: "#F33355", vName: "evilCorp", vIcon: "/img/evil.6c4674fe.svg" },
        { bgColor: "#222222", vName: "ninjaBank", vIcon: "/img/ninja.7a4c8780.svg" },
      ],
    };
  },
  methods:{
    assignColor(event){
      this.cardInfo.cardColor=this.Vendors.find(vendor=>vendor.vName==event.target.value).bgColor
    },
    assignIcon(event){
      this.cardInfo.cardIcon=this.Vendors.find(vendor=>vendor.vName==event.target.value).vIcon
      console.log(this.cardInfo.cardIcon)
    }
  },
  updated() {
    if (this.cardInfo) {
      this.$emit("sendUpdate", { ...this.cardInfo });
    }
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: auto;
  margin-bottom: 50px;
}
</style>