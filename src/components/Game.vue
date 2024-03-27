<script setup lang="ts">
import idioms from '../assets/idioms.json'

const props = defineProps<{
  id: number
}>()

const idiom_en = idioms[props.id].idiom_en
const idiom_ja = idioms[props.id].idiom_ja
</script>

<template>
  <p>{{ idiom_ja }}</p>
  <p>{{ idiom_en }}</p>
</template>

<style scoped>
</style>
