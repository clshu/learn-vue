<script setup lang="ts">
import { ref } from 'vue'
import HandleUserInput from './components/basic/HandleUserInput.vue'
import AttributeBindings from './components/basic/AttributeBindings.vue'
import ConditionalsAndLoops from './components/basic/ConditionalsAndLoops.vue'
import FormBindings from './components/basic/FormBindings.vue'
import SimpleComponent from './components/basic/SimpleComponent.vue'
import MarkdownEditor from './components/practical/MarkdownEditor.vue'

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
    name: 'AttributeBindings',
    component: AttributeBindings,
  },
  {
    name: 'ConditionalsAndLoops',
    component: ConditionalsAndLoops,
  },
  {
    name: 'FormBindings',
    component: FormBindings,
  },
  {
    name: 'SimpleComponent',
    component: SimpleComponent,
  },
]

const practicalComponents = [
  {
    name: 'MarkdownEditor',
    component: MarkdownEditor,
  },
]

const getComponents = (category: string) => {
  switch (category) {
    case 'basic':
      return basicComponents
    case 'practical':
      return practicalComponents
    default:
      return []
  }
}

const findComponent = (category: string, name: string) => {
  const components = getComponents(category)
  return components.find((c) => c.name === name)?.component
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
    <h3>Practical</h3>
    <ul v-for="component in practicalComponents" :key="component.name">
      <li @click="showComponent('practical', component.name)">{{ component.name }}</li>
    </ul>
  </div>
  <div v-else>
    <h3>Chapter: {{ componentName }}</h3>
    <hr />
    <component :is="currentComponent" />
  </div>
</template>

<style scoped></style>
