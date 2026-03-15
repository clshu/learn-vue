<script setup lang="ts">
import { ref, reactive } from 'vue'

const message = ref('Hello World')
const state = reactive({
  count: 0,
})
const isButtonDisabled = ref(false)
</script>

<template>
  <h1>Learn Vue</h1>
  <p>{{ message }}</p>
  <p>Count: {{ state.count }}</p>
  <button @click="state.count++" :disabled="isButtonDisabled">Increment</button>
  <button @click="state.count--" :disabled="isButtonDisabled">Decrement</button>

  <br />
  <button @click="isButtonDisabled = !isButtonDisabled">
    {{ isButtonDisabled ? 'Enable' : 'Disable' }} Counter Buttons
  </button>
  <hr />
  <p v-if="state.count === 3">Count is 3</p>
</template>

<style scoped></style>
