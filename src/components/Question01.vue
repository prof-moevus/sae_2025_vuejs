<script setup>
import {ref} from 'vue'

const answer = ref("")
</script>

<template>
  <h2>Question 01</h2>
  <p class="question">Quel est la couleur du beurre ?</p>
  <label for="answer">Réponse : </label>
  <input id="answer" v-model="answer"/>
  <p class="form-invalid" v-if="answer.length>1">Votre réponse doit faire un caractère</p>


  <div class="display-answers">
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
  </div>
  <p>fin du quiz.</p>
</template>

<style scoped>
.form-invalid {
  font-size: 0.8em;
  color: #bc3c3c;
}

.display-answers {
  margin: 1em;
  padding: 0.5em;
  text-align: center;
  background-color: #2c3e50;
  color: white;
  box-shadow: #282828 3px 5px 5px 3px;
}
</style>