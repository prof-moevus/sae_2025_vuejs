<template>
  <div>
    <h3>Liste d'articles</h3>

    <!-- Liste d'éléments avec références -->
    <div class="items-container">
      <div
          v-for="(item, index) in items"
          :key="item.id"
          :ref="el => { if(el) itemRefs[index] = el }"
          class="item-card"
          tabindex="0"
      >
        <h4>{{ item.name }}</h4>
        <p>{{ item.description }}</p>
      </div>
    </div>

    <!-- Boutons de navigation -->
    <div class="controls">
      <button @click="scrollToItem(0)">Premier article</button>
      <button @click="scrollToItem(1)">Deuxième article</button>
      <button @click="scrollToItem(2)">Troisième article</button>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, onBeforeUpdate } from 'vue'

const items = ref([
  {
    id: 1,
    name: 'Casque audio',
    description: 'Casque sans fil avec réduction de bruit active'
  },
  {
    id: 2,
    name: 'Smartphone',
    description: 'Téléphone intelligent avec appareil photo 48MP'
  },
  {
    id: 3,
    name: 'Ordinateur portable',
    description: 'Ultrabook léger avec 16Go de RAM'
  }
])

// Tableau pour stocker les références aux éléments DOM
const itemRefs = reactive([])

// IMPORTANT: Réinitialiser les références avant chaque mise à jour
onBeforeUpdate(() => {
  itemRefs.length = 0
})

// POINT IMPORTANT la fonction ci-dessous accède directement au DOM
// grâce à l'utilisation de `ref`.
// Le but est de faire défiler jusqu'à un élément et lui donner le focus
function scrollToItem(index) {
  if (index >= 0 && index < itemRefs.length) {
    // Faire défiler la page jusqu'à l'élément
    itemRefs[index].scrollIntoView({
      behavior: 'smooth',  // Animation fluide
      block: 'center'      // Centrer l'élément dans la fenêtre
    })

    // Donner le focus à l'élément (pour l'accessibilité)
    itemRefs[index].focus()
  }
}
</script>

<style scoped>
.items-container {
  height: 200px;
  overflow-y: scroll;
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 15px;
}

.item-card {
  margin-bottom: 15px;
  padding: 15px;
  border-radius: 8px;
  background-color: #f5f5f5;
}

.item-card:focus {
  outline: 3px solid #42b983;
  background-color: #ebfff0;
}

.controls {
  display: flex;
  gap: 10px;
}

button {
  padding: 8px 12px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
