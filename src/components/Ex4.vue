<script setup>
import { ref } from 'vue'

const items = ref(['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'])
const newItem = ref('')

function del(index) {
  items.value.splice(index, 1)
}

function addItem() {
  if (newItem.value.trim() !== '') {
    items.value.push(newItem.value.trim())
    newItem.value = ''
  }
}
</script>

<template>
  <h2>Shopping Cart</h2>

  <ul>
    <li v-for="(item, index) in items" :key="index">
      {{ item }} <button @click="del(index)">Delete!</button>
    </li>
  </ul> 

  <!-- Input triggers addItem on Enter key or button click -->
  <input type = "text" v-model="newItem" @keyup.enter = "addItem">
  <button @click = "addItem">Add!</button>
</template>