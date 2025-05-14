<script setup>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  onErrorCaptured
} from 'vue'
import { ref } from 'vue'

// Avant le montage du composant
onBeforeMount(() => {
  console.log('Le composant va être monté')
})

// Après le montage (DOM accessible)
onMounted(() => {
  console.log('Le composant est monté')
  // Idéal pour les initialisations qui nécessitent l'accès au DOM
  // - Appels API
  // - Configuration de bibliothèques tierces
  // - Ajout d'écouteurs d'événements
})

// Avant une mise à jour
onBeforeUpdate(() => {
  console.log('Le composant va être mis à jour')
})

// Après une mise à jour
onUpdated(() => {
  console.log('Le composant a été mis à jour')
  // Le DOM est maintenant à jour avec les changements
  // ⚠️ Évitez de modifier l'état ici, cela pourrait créer une boucle infinie

  setTimeout(()=>{
    test.value = !test.value
  }, 1000)
})

// Avant la destruction
onBeforeUnmount(() => {
  console.log('Le composant va être détruit')
})

// Après la destruction
onUnmounted(() => {
  console.log('Le composant a été détruit')
  // Idéal pour le nettoyage
  // - Supprimer les écouteurs d'événements
  // - Annuler les requêtes en cours
  // - Arrêter les timers
})

// Capture des erreurs dans les composants descendants
onErrorCaptured((err, instance, info) => {
  console.error('Erreur capturée:', err)
  // Retourner false empêche la propagation de l'erreur
  return false
})

const test = ref(true)
</script>

<template>

  <input v-model="test" type="checkbox"/>
  <p v-if="test">Update</p>
</template>
