<script setup>
import { ref } from 'vue'

const items = ref([
  { id: 12123, name: 'Item 1' },
  { id: 4232, name: 'Item 2' },
  { id: 3994, name: 'Item 3' },
  { id: 422354, name: 'Item 4' }
])
</script>


<template>
  <ul>
    <!-- Itération sur un tableau -->
    <li v-for="item in items" :key="item.id">
      {{ item.name }}
    </li>
  </ul>
</template>

