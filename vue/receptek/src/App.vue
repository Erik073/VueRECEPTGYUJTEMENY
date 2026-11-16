<script setup>
import { ref } from 'vue'
import Recept from './components/Recept.vue'
import UjRecept from './components/UjRecept.vue'

const currentView = ref('recipes')

function showRecipes() {
  currentView.value = 'recipes'
}
function showNewRecipe() {
  currentView.value = 'new-recipe'
}
function handleAddRecipe() {
  currentView.value = 'recipes'
}
</script>

<template>
  <header>
    <nav class="navbar bg-white border-bottom py-3">
      <div class="container d-flex justify-content-between align-items-center">
        <button
          type="button"
          class="navbar-brand d-flex align-items-center gap-2 fw-bold text-dark m-0 btn btn-link p-0 text-decoration-none"
          @click="showRecipes"
        >
          <span class="r-icon d-inline-flex align-items-center justify-content-center text-white fw-bold rounded-3">
            R
          </span>
          Receptkönyv
        </button>
        <div class="d-flex align-items-center gap-4">
          <button type="button" class="nav-link text-secondary fw-medium p-0 btn btn-link" @click="showRecipes">
            Receptek
          </button>
          <button type="button" class="btn btn-success text-white fw-medium px-3 py-2 rounded-3" @click="showNewRecipe">
            + Új recept
          </button>
        </div>
      </div>
    </nav>
  </header>

  <main class="container my-4">
    <Recept v-if="currentView === 'recipes'" />
    <UjRecept v-else @addRecipe="handleAddRecipe" />
  </main>

  <footer class="container bg-white border-top py-3 mt-auto">
    <div class="container d-flex justify-content-between align-items-center">
      <p class="mb-0">Receptkönyv</p>
      <p class="mb-0">Főzz örömmel, oszd meg szeretettel.</p>
    </div>
  </footer>
</template>

<style scoped>
.r-icon {
  background-color: #3d7a5b;
  width: 34px;
  height: 34px;
  font-size: 1rem;
  box-shadow: 0 2px 5px rgba(61, 122, 91, 0.25);
}
</style>
