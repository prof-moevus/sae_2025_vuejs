<script setup>
import {ref} from 'vue'
import Question01 from "@/components/Question01.vue";
import DemoCyclesDeVie from "@/components/DemoCyclesDeVie.vue";
import DemoListRendering from "@/components/DemoListRendering.vue";
import DemoVForAndRef from "@/components/DemoVForAndRef.vue";

const showQuestion01 = ref(false);
function myLog() {
  console.log("DB 8764: " + showQuestion01.value);
}
</script>

<template>
<h1> Introduction à Vue.js pour le de web app</h1>

  <h2>Liste des exemples</h2>
    <div>
      <label for="Question01">Question 01 : </label>
      <input v-model="showQuestion01" id="Question01" type="checkbox" name="Question01">
    </div>

  <div class="exemple">
<!--    <Question01 v-if="showQuestion01"/>-->
<!--<DemoCyclesDeVie v-if="showQuestion01"></DemoCyclesDeVie>-->
<!--    <DemoListRendering>-->
    <DemoVForAndRef/>
  </div>

</template>

<style>
body {
  background-color: #a3a3a3;
}
.exemple {
  border: 8px solid #000000;
  margin: 20px auto;
  padding: 10px;
}
</style>