<template>
  <div class="container">
    <header class="title">Game Pokemon</header>
    <ControllerComponents class="space "/>
  </div>
</template>

<script setup>
import ControllerComponents from './components/ControllerComponent.vue'


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

.title {
  background-image: linear-gradient(to right, #dcfbf3,#1c5880,#e76c03, brown);
  color: white;
  height: 10%;
  text-align: center;
  padding: 10px;
  font-size: 24px;
  font-family: cursive;
  width: 100%;
}
.space{
  margin-top: 3%;
}

</style>
