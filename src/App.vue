<template>
  <div>
    <h1
      :style="{ color }">
      Hello {{name}}
    </h1>
    <input 
      type="text" 
      v-model="name">
    <button 
      @click="handleClick">
      Alert!
    </button>
    <h1>My List</h1>
    <input
      @keyup.enter="addFood" 
      type="text" 
      v-model="currentFood" >
    <button 
      @click="addFood">
      add
    </button>

    <food-list 
      @stop="handleStop"
      :foods="foods"/>
  </div>
</template>

<script>
import FoodList from './components/FoodList'

export default {
  components: { FoodList },
  data: () => ({
      name: 'Ivan',
      color: 'tomato',
      foods: ['Maçã', 'Pera'],
      currentFood: ''
  }),
  methods: {
    handleClick() {
      window.alert('Clicado!')
    },
    addFood() {
      this.foods.push(this.currentFood)
      this.currentFood = ''
    },
    handleStop(event) {
      window.alert('Ta Cheio => ' + event);
    }
  },
}
</script>

<style>

</style>
