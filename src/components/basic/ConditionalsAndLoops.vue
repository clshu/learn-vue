<script setup lang="ts">
import { ref } from 'vue'

const show = ref(true)
const list = ref([1, 2, 3, 4, 5])
</script>

<template>
  <button @click="show = !show">Toggle List</button>
  <button @click="list.push(list.length + 1)">Push Number</button>
  <button @click="list.pop()">Pop Number</button>
  <button @click="list.reverse()">Reverse List</button>
  <ul v-if="show && list.length">
    <li v-for="item in list" :key="item">{{ item }}</li>
  </ul>
  <p v-else-if="show && list.length === 0">List is empty</p>
  <p v-else>List is hidden</p>
</template>
