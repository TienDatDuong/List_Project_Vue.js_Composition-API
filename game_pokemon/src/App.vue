<template>
  <div class="container">
    <header-components @getCount="getCount" :isPlaying="isPlaying"/>
    <ControllerComponents v-if="!isPlaying" @playing="playing"/>
    <CardsComponent v-if="isPlaying" :pokemons="pokemons"/>
  </div>
</template>

<script setup>
import ControllerComponents from './components/ControllerComponent.vue'
import HeaderComponents from './components/HeaderComponent'
import CardsComponent from './components/CardsComposnet'
import {ref} from "vue";
import {ElMessage} from "element-plus";

const isPlaying = ref(false)
const pokemons = ref(0)

const getCount = (num) =>{
  pokemons.value = num
}

const playing = () => {
  if(pokemons.value > 0){
     isPlaying.value = true
  }else {
    ElMessage({
      message: 'Please select the number of pokemon',
      type: "success"
    });
  }
}


</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.container {
  min-width: 100vw;
  min-height: 100vh;
  background-image: url('./assets/images/background.jpg');
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  flex-direction: column;

  align-items: center;
}

.space{
  margin-top: 3%;
}

</style>
