<script setup lang="ts">
import { ref, reactive } from 'vue'

const message = ref('Hello World')
const state = reactive({
  count: 0,
})
</script>

<template>
  <h1>Learn Vue</h1>
  <p>{{ message }}</p>
  <p>{{ state.count }}</p>
  <button @click="state.count++">Increment</button>
  <button @click="state.count--">Decrement</button>
</template>

<style scoped></style>
