<template>
  <ul>
    <li v-for="(food, index) in foods" :key="`${food}-${index}`">{{ food }}</li>
  </ul>
</template>

<script>
const MAX_CONTENT = 5;
  export default {
    props: {
      foods: {type: Array, default: () => []}
    },
    watch: {
      foods() {
        if(this.foods.length > MAX_CONTENT) {
          this.$emit('stop', 'Para aí mano, já deu com isso aí');
          this.foods.pop();
          localStorage.setItem('foods', JSON.stringify(this.foods));
        }
      }
    }
  }
</script>