<script setup lang="ts">
import { ref } from 'vue'

const message = ref('Hello World')
const toggled = ref(false)

function reverseMessage() {
  message.value = message.value.split('').reverse().join('')
}

function removeChar(char: string) {
  message.value = message.value.replace(char, '')
}

function appendChar(char: string) {
  message.value += char
}

function toggle() {
  if (toggled.value) {
    removeChar('!')
  } else {
    appendChar('!')
  }
  toggled.value = !toggled.value
}

function notify() {
  alert('navigation was prevented.')
}
</script>

<template>
  <p>{{ message }}</p>
  <button @click="reverseMessage">Reverse</button>
  <button @click="toggle">{{ toggled ? 'Remove' : 'Append' }} !</button>
  <a href="https://vuejs.org" @click.prevent="notify"> A link with e.preventDefault() </a>
</template>

<style scoped>
button,
a {
  display: block;
  margin-bottom: 1em;
}
</style>
