<template>
  <div class="container_control">
    <el-button type="info">Start game</el-button>
    <div class="space">
      <el-radio-group v-model="radio1">
        <el-radio type="success" label="1" size="large" border>4</el-radio>
        <el-radio label="2" size="large" border>6</el-radio>
        <el-radio label="3" size="large" border>8</el-radio>
        <el-radio label="4" size="large" border>10</el-radio>
      </el-radio-group>
    </div>
  </div>
</template>
<script setup>
import {ref} from "vue";

const radio1 = ref('1')

</script>
<style scoped>
.container_control {
  display: flex;
  align-items: center;
  flex-direction: column;
}

</style>