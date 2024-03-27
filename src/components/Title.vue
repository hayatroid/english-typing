<script setup lang="ts">
const emits = defineEmits<{
  gameStart: []
}>()
</script>

<template>
  <button @click="emits('gameStart')">ゲームスタート！</button>
</template>

<style scoped>
</style>
