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
      <select v-model="cardInfo.vendor">
        <option v-for="vendor in Vendors" :key="vendor.vName" v-on:click.self="cardInfo.cardColor = vendor.bgColor">
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
        { bgColor: "red", vName: "bitcoin", vIcon: "" },
        { bgColor: "yellow", vName: "blockChain", vIcon: "" },
        { bgColor: "blue", vName: "evilCorp", vIcon: "" },
        { bgColor: "green", vName: "ninjaBank", vIcon: "" },
      ],
    };
  },
  methods:{
    assignColor(color){
      this.cardInfo.cardColor=color;
      console.log(this.cardInfo.cardColor)
    }
  },
  updated() {
    if (this.cardInfo) {
      this.$emit("sendUpdate", { ...this.cardInfo });
    }
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: auto;
  margin-bottom: 50px;
}
</style>