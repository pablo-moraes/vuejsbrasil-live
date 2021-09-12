<template>
  <div>
    <br>
    <input type="text" v-model="contentFood" @keyup.enter="addFood">
    <button @click="addFood">
      Adicionar
    </button>
    <food-list @stop="handleStop" :foods="foods"/>
  </div>
</template>
<script>
import FoodList from './components/FoodList'
export default {
  components: { FoodList },
  data: () => ({
      foods: JSON.parse(localStorage.getItem('foods')) || [],
      contentFood: ''
  }),
  methods:  {
    handleStop(payload) {
      console.log(payload);
      window.alert(payload);
    },
    addFood() {
      this.foods.push(this.contentFood);
      localStorage.setItem('foods', JSON.stringify(this.foods));
      this.contentFood = '';
    }
  }
}
</script>
<style>
body {
  background: #2c3e50;
  color: white;
}

div {
  margin-inline: auto;
}
</style>
