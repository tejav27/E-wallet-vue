<template>
  <div>
    <form>
      <label for="card-number">CARD NUMBER</label>
      <input
        type="number"
        name="card-number"
        id="card-number"
        placeholder="Enter card number"
        v-model="cardInfo.cardNumber"
        required="required"
      />
      <label for="card-name">CARDHOLDER NAME</label>
      <input
        type="text"
        name="card-name"
        id="card-name"
        placeholder="Enter card name"
        v-model="cardInfo.name"
        required
      />
      <label for="month">MONTH</label>
      <input
        type="number"
        name="month"
        id="month"
        placeholder="Month"
        v-model="cardInfo.validMonth"
        min="1"
        max="12"
      />
      <label for="year">YEAR</label>
      <input
        type="number"
        name="year"
        id="year"
        placeholder="Year"
        v-model="cardInfo.validYear"
        min="2022"
      />
      <label for="vendor">Vendor</label>
      <select v-model="cardInfo.vendor" v-on:change="assignColor($event); assignIcon($event)" id="vendor">
        <option v-for="vendor in Vendors" :key="vendor.bgColor" >
          {{ vendor.vName }}
        </option>
      </select>
      <button type="reset">Reset</button>
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
        { bgColor: "#FFAE34", vName: "Bitcoin", vIcon:"../assets/bitcoin.svg" },
        { bgColor: "#8B58F9", vName: "BlockChain", vIcon: "/img/blockchain.a26084d8.svg" },
        { bgColor: "#F33355", vName: "EvilCorp", vIcon: "/img/evil.6c4674fe.svg" },
        { bgColor: "#222222", vName: "NinjaBank", vIcon: "/img/ninja.7a4c8780.svg" },
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
    },
    sendnewCardInfo(){
      this.$emit("sendUpdate", { ...this.cardInfo });
    }
  },
  computed:{
    newCardnumber(){
      return this.cardInfo.cardNumber
        }
  },
   updated() {
    if(this.cardInfo)
      this.$emit("sendUpdate", { ...this.cardInfo });
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
button{
  margin-top: 10px;
}
</style>