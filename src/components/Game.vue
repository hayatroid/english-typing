<script setup lang="ts">
import { computed, ref } from 'vue'
import idioms from '../assets/idioms.json'

const props = defineProps<{
  id: number
}>()

const emits = defineEmits<{
  complete: []
  allComplete: []
}>()

const word = idioms[props.id].word
const idiom_en = idioms[props.id].idiom_en
const idiom_ja = idioms[props.id].idiom_ja

const start = idiom_en.indexOf(word)
const pos = ref<number>(start + 1)
const end = start + word.length

const idiom_en_converted = computed<string>(() => {
  let res = ''
  res += idiom_en.slice(0, start)
  res += `<span style="color: red">${idiom_en.slice(start, pos.value)}</span>`
  res += `<span style="color: pink">${'-'.repeat(end - pos.value)}</span>`
  res += idiom_en.slice(end)
  return res
})

const onKeyDown = (e: KeyboardEvent) => {
  if (pos.value < end && e.key == idiom_en[pos.value] && !e.repeat) {
    pos.value++
  }
  if (pos.value == end) {
    if (props.id + 1 < idioms.length) {
      emits('complete')
    } else {
      emits('allComplete')
    }
  }
}
document.addEventListener('keydown', onKeyDown)
</script>

<template>
  <p>{{ idiom_ja }}</p>
  <p v-html="idiom_en_converted"></p>
</template>

<style scoped>
</style>
