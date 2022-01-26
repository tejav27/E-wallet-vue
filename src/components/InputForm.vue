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
      <div class="month-year">
        <div class="month">
        <label for="month">MONTH</label>
          <!-- <input
            type="number"
            name="month"
            id="month"
            placeholder="Month"
            v-model="cardInfo.validMonth"
            min="1"
            max="12"
          /> -->
          <select
        v-model="cardInfo.validMonth"
        id="month"
      >
        <option v-for="month in 12" :key="month">
          {{ month }}
        </option>
      </select>
        </div>
        <div class="year">
          <label for="year">YEAR</label>
          <!-- <input
            type="number"
            name="year"
            id="year"
            placeholder="Year"
            v-model="cardInfo.validYear"
            min="22"
          /> -->
          <select
        v-model="cardInfo.validYear"
        id="year"
      >
        <option v-for="year in years" :key="year">
          {{ year }}
        </option>
      </select>
        </div>
      </div>
      <label for="vendor">Vendor</label>
      <select
        v-model="cardInfo.vendor"
        v-on:change="
          assignColor($event);
          assignIcon($event);
        "
        id="vendor"
      >
        <option v-for="vendor in Vendors" :key="vendor.bgColor">
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
        cardIcon: "",
        cardNumber: "",
        name: "",
        validMonth: null,
        validYear: null,
      },
      years:[22, 23, 24, 25, 26, 27, 28],
      Vendors: [
        { bgColor: "#FFAE34", vName: "bitcoin", vIcon: "bitcoin.svg" },
        { bgColor: "#8B58F9", vName: "blockchain", vIcon: "blockchain.svg" },
        { bgColor: "#F33355", vName: "evil", vIcon: "evil.svg" },
        { bgColor: "#222222", vName: "ninja", vIcon: "ninja.svg" },
      ],
    };
  },
  methods: {
    assignColor(event) {
      console.log(this.Number);
      this.cardInfo.cardColor = this.Vendors.find(
        (vendor) => vendor.vName == event.target.value
      ).bgColor;
    },
    assignIcon(event) {
      this.cardInfo.cardIcon = this.Vendors.find(
        (vendor) => vendor.vName == event.target.value
      ).vIcon;
    },
    sendnewCardInfo() {
      this.$emit("sendUpdate", { ...this.cardInfo });
    },
  },
  computed: {
    newCardnumber() {
      return this.cardInfo.cardNumber;
    },
    Name() {
      return this.cardInfo.name.toUpperCase();
    },
  },
  updated() {
    if (this.cardInfo) this.$emit("sendUpdate", { ...this.cardInfo });
    this.cardInfo.name = this.Name;
  },
};
</script>

<style scoped lang="scss">
*{
  box-sizing: border-box;
}
form {
  display: flex;
  flex-direction: column;
  max-width: 400px;
  width: 20rem;
  margin: 1rem;
  place-items: center;
  margin-bottom: 50px;
}
input {
  place-items: center;
  max-width: 350px;
  height: 40px;
  width: 20rem;
  border-radius: 6px;
  padding: 10px;
  margin: 10px;
  font-weight: bolder;
  &:focus{
    background-color: powderblue;
    color: black;
  }
}
.month-year {
  display: flex;
  max-width: 400px;
  width: 20rem;
  justify-content: space-around;
}
.month,
.year {
  display: flex;
  flex-direction: column;
  width: 10rem;
  select{
    max-width: 9.8rem; 
    margin: 0.5rem;
    margin-left: 0px;   
  }
}
select{
  width: 100%;
  border: solid black 2px;
  height: 40px;
  border-radius: 6px;
  font-weight: bolder;
  font-size: 1rem;
  padding: 10px;
  margin: 10px;
  option{
    place-items: center;
    color: whitesmoke;
    background-color: rgb(31, 45, 54);
    &:hover{
      background-color: rgb(10, 56, 109)
    }
  }
}
button {
  margin-top: 20px;
  padding: 15px 25px;
  align-self: start;
  background-color: dimgrey;

  &:hover{
    padding: 15px 40px;
    color: rgb(204, 13, 13);
    background-color: white;
    font-size: 1.25rem;
}

}
</style>