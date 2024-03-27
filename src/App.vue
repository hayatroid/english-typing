<script setup lang="ts">
import { ref } from 'vue'
import Title from './components/Title.vue'
import Game from './components/Game.vue'

const id = ref<number>(0)
const is_playing = ref<boolean>(false)

const gameStart = () => {
  id.value = 0
  is_playing.value = true
}
</script>

<template>
  <Title v-if="!is_playing" @game-start="gameStart()" />
  <Game v-else :id="id" :key="id" @complete="id++" />
</template>

<style scoped>
</style>
