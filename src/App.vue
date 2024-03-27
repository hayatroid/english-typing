<script setup lang="ts">
import { ref } from 'vue'
import Game from './components/Game.vue'

const id = ref<number>(0)
</script>

<template>
  <Game :id="id" :key="id" @complete="id++" />
</template>

<style scoped>
</style>
