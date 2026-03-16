<script setup lang="ts">
import { ref } from 'vue'

const text = ref('Edit me')
const checked = ref(true)
const names = ['Jack', 'John', 'Jane', 'Mike']
const options = ['One', 'Two', 'Three']
const selectList = ['A', 'B', 'C']
const checkedNames = ref(['Jack'])
const picked = ref('One')
const selected = ref('A')
const multiSelected = ref([selectList[0]])
</script>

<template>
  <h2>Text Input</h2>
  <input v-model="text" />
  <p>{{ text }}</p>

  <h2>Checkbox</h2>
  <input type="checkbox" id="checkbox" v-model="checked" />
  <label for="checkbox">Checked: {{ checked }}</label>

  <h2>Checkboxes (Multiple)</h2>
  <div v-for="(name, index) in names" :key="index">
    <input type="checkbox" :id="name.toLowerCase()" v-model="checkedNames" :value="name" />
    <label :for="name.toLowerCase()">{{ name }}</label>
  </div>
  <p>Checked: {{ checkedNames }}</p>

  <h2>Radio</h2>
  <div v-for="(option, index) in options" :key="index">
    <input type="radio" :id="option.toLowerCase()" v-model="picked" :value="option" />
    <label :for="option.toLowerCase()">{{ option }}</label>
  </div>

  <h2>Select</h2>
  <select v-model="selected">
    <option disabled value="">Please select one</option>
    <div v-for="(item, index) in selectList" :key="index">
      <option>{{ item }}</option>
    </div>
  </select>
  <p>Selected: {{ selected }}</p>

  <h2>Multi Select</h2>
  <select v-model="multiSelected" multiple style="width: 100px">
    <div v-for="(item, index) in selectList" :key="index">
      <option>{{ item }}</option>
    </div>
  </select>
  <p>Selected: {{ multiSelected }}</p>
</template>
