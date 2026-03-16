<script setup lang="ts">
import { ref } from 'vue'
import TodoItem from './TodoItem.vue'

const groceryList = ref([
  { id: 0, text: 'Vegetables' },
  { id: 1, text: 'Cheese' },
  { id: 2, text: 'Whatever else humans eat' },
])
</script>

<template>
  <ol>
    <TodoItem v-for="item in groceryList" :key="item.id" :todo="item" />
  </ol>
</template>
