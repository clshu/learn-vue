<script setup lang="ts">
import { ref } from 'vue'
import HandleUserInput from './components/basic/HandleUserInput.vue'
import AttributeBinding from './components/basic/AttributeBinding.vue'
import ConditionalAndLoops from './components/basic/ConditionalAndLoops.vue'

const componentName = ref('')
const currentComponent = ref<Component | null>(null)
const showHomePage = ref(true)
const currentCategory = ref('basic')

function showComponent(category: string, name: string) {
  currentCategory.value = category
  componentName.value = name
  currentComponent.value = findComponent(category, name)
  showHomePage.value = false
}
const basicComponents = [
  {
    name: 'HandleUserInput',
    component: HandleUserInput,
  },
  {
    name: 'AttributeBinding',
    component: AttributeBinding,
  },
  {
    name: 'ConditionalAndLoops',
    component: ConditionalAndLoops,
  },
]

const findComponent = (category: string, name: string) => {
  if (category === 'basic') {
    return basicComponents.find((c) => c.name === name)?.component
  } else {
    return null
  }
}
</script>

<template>
  <button @click="showHomePage = true">Home</button>
  <hr />
  <h1 style="display: flex; justify-content: center; align-items: center">Vue Examples</h1>

  <div v-if="showHomePage">
    <h3>Basic</h3>
    <ul v-for="component in basicComponents" :key="component.name">
      <li @click="showComponent('basic', component.name)">{{ component.name }}</li>
    </ul>
  </div>
  <div v-else>
    <h3>Chapter: {{ componentName }}</h3>
    <hr />
    <component :is="currentComponent" />
  </div>
</template>

<style scoped></style>
