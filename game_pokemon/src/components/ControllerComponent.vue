<template>
  <div class="container_control">
    <button type="info" class="btn_start" @click="handleStart">Start game</button>
  </div>
</template>
<script setup>
import defineEmits from 'vue'

const emit = defineEmits(['playing'])

const handleStart = () => {
  emit('playing')
}

</script>
<style scoped>
.container_control {
  display: flex;
  min-width: 100vw;
  min-height: 100vh;
  align-items: center;
  justify-content: center;
  transform: translateY(50%);
  transform: translateX(2%);
}
.btn_start{
  margin-bottom: 4%;
  border: none;
  padding: 9px 65px;
  border-radius: 2%;
  font-size: 24px;
  background-color: #916c47;
  color: #284e7f;
  font-family: monospace;
  z-index: 1;
  box-shadow: 5px 10px;
}
.btn_start:hover{
  background-color: #284e7f;
  color: black;
}
</style>