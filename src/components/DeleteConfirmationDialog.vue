<template>
  <div class="delete-dialog">
      <p>Are you sure you want to delete this card?</p>
      <div class="buttons">
      <button @click="confirmDeletion">Yes</button>
      <button @click="goBack">No</button>
      </div>
  </div>
</template>

<script>
export default {
    data(){return{
        deleteThisCard:null
    }},
methods:{
    confirmDeletion(){
        this.deleteThisCard = true 
        this.$emit('confirmDeletion',this.deleteThisCard)
    },
    goBack(){
        this.$emit('goBack')
    }
}
}
</script>

<style scoped lang="scss">
.delete-dialog{
    position: absolute;
    top: 200px;
  padding: 10px;
  z-index: 10;
  background-color:rgb(80, 73, 73);
  border-radius: 5px;
  border: #3D3D3D 2px;
  color: beige;
.buttons{
    display: flex;
}
button{
    background-color:papayawhip;
    margin: 10px;
    padding: 10px 20px;
}
button:hover{
    background-color: maroon;
    color: mintcream;
}
}
</style>