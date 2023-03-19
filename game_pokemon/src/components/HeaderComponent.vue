<template>
  <div class="container_header">
    <header class="title">Game Pokemon</header>
    <el-radio-group v-model="radio1" style="width: 23%" v-if="!props.isPlaying">
      <el-radio-button @click="getNumber(4)" value="4" size="medium" label="4 cards"></el-radio-button>
      <el-radio-button @click="getNumber(6)" value="6" label="6 cards"></el-radio-button>
      <el-radio-button @click="getNumber(8)" value="8" label="8 cards"></el-radio-button>
      <el-radio-button @click="getNumber(10)" value="10" label="10 cards"></el-radio-button>
    </el-radio-group>
    <div v-else>
      <el-button type="primary" style="font-size: 16px" >
        Back
      </el-button>
    </div>
  </div>
</template>
<script setup>
import {ref, defineEmits,defineProps} from "vue";
import { ElMessage } from "element-plus";


const emit = defineEmits(['getCount'])
const radio1 = ref('2')

const props = defineProps({
  isPlaying:{
    type:Boolean,
    default: false
  }
})

const getNumber = (num) => {
  if(props.isPlaying){
    ElMessage({
      message: 'fdgdfg',
      type: "success"
    });
  } else {
    emit('getCount', num)
  }
}

</script>

<style scoped>
.container_header {
  width: 100%;
  display: flex;
  flex-direction: row;
  background-image: linear-gradient(to right, #dcfbf3, #1c5880, #e76c03, brown);
  color: #000;
  height: 10%;
  text-align: left;
  padding: 10px;
  font-size: 24px;
  font-family: cursive;
}

.title {
  display: flex;
  flex: 1;
}
</style>