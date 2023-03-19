<template>
  <div class="container_img">
    <div class="card" @click="changeCard(idx,item)" v-for="(item,idx) in getRamdomPokemon" :key="idx">
      <div class="flip-card-inner" :class="{flip: hanld[idx]}">
        <div class="flip-card-front">
          <img :src="require('@/assets/pokemonImage/icon_back.png')"/>
        </div>
        <div class="flip-card-back">
          <img :src="require(`@/assets/pokemonImage/${item}.png`)"/>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>

import defineProps, {computed, ref} from "vue";

const typePokemon = ref(64)
const pokemonArray1 = ref([])
const pokemonArray2 = ref([])
const pokemonArray = ref([])
const hanld = ref([])
const newArray = ref([])

const props = defineProps({
  pokemons: {
    type: Number,
    default: 0
  }
})


// eslint-disable-next-line vue/return-in-computed-property
const getRamdomPokemon = computed(() => {
  if (props.pokemons) {
    for (let i = 0; i < props.pokemons; i++) {
      const random = Math.floor(Math.random() * typePokemon.value) + 1
      // eslint-disable-next-line vue/no-side-effects-in-computed-properties
      pokemonArray1.value.push(random)
      // eslint-disable-next-line vue/no-side-effects-in-computed-properties
      pokemonArray2.value.push(random)
    }
    // eslint-disable-next-line vue/no-side-effects-in-computed-properties
    pokemonArray.value = pokemonArray1.value.concat(pokemonArray2.value)
    // eslint-disable-next-line vue/no-side-effects-in-computed-properties
    pokemonArray.value.sort(() => Math.random() - 0.5)
    return pokemonArray.value
  }
})

const changeCard = (idx, pokemon) => {
  hanld.value[idx] = !hanld.value[idx]
  const index = newArray.value.findIndex(i => {
    i.pokemon === newArray[idx]
  })
  if (index < 0) {
    newArray.value.push({pokemon,idx})
  }
  if (newArray.value.length % 2 == 0) {
    setTimeout(()=>{
      for (let i = 0; i < newArray.value.length; i += 2) {
        const card1 = newArray.value[i];
        const card2 = newArray.value[i + 1];
        if (card1.pokemon !== card2.pokemon) {
          hanld.value[newArray.value[i].idx] = !hanld.value[newArray.value[i].idx];
          hanld.value[newArray.value[i + 1].idx] = !hanld.value[newArray.value[i + 1].idx];
        }
      }
      newArray.value = []
    },350)
  }
}

</script>
<style scoped>
.container_img {
  max-width: 60vw;
  margin: auto;
  display: grid;
  grid-template-columns: auto auto auto auto;
  align-items: center;
  justify-content: center;
}

.card {
  background-color: transparent;
  width: 100px;
  height: 120px;
  margin: 5px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}

.flip-card-inner.flip {
  transform: rotatey(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #dcfbf3;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
}

.flip-card-back {
  background-color: #dcfbf3;
  display: flex;
  justify-content: center;
  align-items: center;
  transform: rotateY(180deg);
  border-radius: 5px;
}

img {
  width: 90px;
  height: 80px;
}
</style>