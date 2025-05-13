<script setup>
import {ref} from 'vue'

const answer = ref('B')
</script>

<template>
  <h2>Question 01</h2>
  <p v-if="answer === 'A'">
    C'est A.
  </p>
  <h2 v-else-if="answer === 'B'">
    C'est B.
  </h2>
  <div v-else-if="answer === 'C'">
    C'est C.
  </div>
  <div v-else>
    Ce n'est ni A, ni B, ni C.
  </div>
  <p>fin du quiz.</p>
</template>

<style scoped>

</style>