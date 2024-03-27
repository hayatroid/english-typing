<script setup lang="ts">
import idioms from '../assets/idioms.json'

const props = defineProps<{
  id: number
}>()

const word = idioms[props.id].word
const idiom_en = idioms[props.id].idiom_en
const idiom_ja = idioms[props.id].idiom_ja

const start = idiom_en.indexOf(word)
const pos = start + 1
const end = start + word.length
</script>

<template>
  <p>{{ idiom_ja }}</p>
  <p>{{ idiom_en }}</p>
</template>

<style scoped>
</style>
