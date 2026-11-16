<script setup>
import { ref, watch } from 'vue'

import husleves from './assets/husleves.webp'
import paprikaskrumpli from './assets/paprikaskrumpli.jpg'
import Recept from './components/Recept.vue'
import UjRecept from './components/UjRecept.vue'

const STORAGE_KEY = 'recept-gyujtemeny'

const defaultRecipes = [
  {
    id: 1,
    name: 'Gulyásleves',
    image: husleves,
    description: 'A magyar konyha egyik legismertebb levese, marhahússal, zöldségekkel és fűszerpaprikával.',
    difficulty: 'Közepes',
    time: 50
  },
  {
    id: 2,
    name: 'Paprikás krumpli',
    image: paprikaskrumpli,
    description: 'Tartalmas egytálétel burgonyából, kolbásszal, hagymával és fűszerpaprikával.',
    difficulty: 'Könnyű',
    time: 60
  },
  {
    id: 3,
    name: 'Palacsinta',
    image: husleves,
    description: 'Vékony, könnyű tésztájú palacsinta, amely lekvárral, kakaóval vagy túróval is megtölthető.',
    difficulty: 'Nehéz',
    time: 20
  }
]

const recipes = ref(loadRecipes())
const showForm = ref(false)

function loadRecipes() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY)
    if (!saved) return [...defaultRecipes]

    const parsed = JSON.parse(saved)
    return Array.isArray(parsed) && parsed.length ? parsed : [...defaultRecipes]
  } catch (error) {
    console.error('Hiba a mentett adatok betöltésekor:', error)
    return [...defaultRecipes]
  }
}

function saveRecipes() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(recipes.value))
  } catch (error) {
    console.error('Hiba a mentéskor:', error)
  }
}

watch(recipes, saveRecipes, { deep: true })

function addRecipe(recipe) {
  recipes.value = [
    ...recipes.value,
    {
      ...recipe,
      id: Date.now()
    }
  ]
  showForm.value = false
}
</script>

<template>
  <header>
    <nav class="navbar bg-white border-bottom py-3">
      <div class="container d-flex justify-content-between align-items-center">
        <button type="button"
          class="navbar-brand d-flex align-items-center gap-2 fw-bold text-dark m-0 btn btn-link p-0 text-decoration-none"
          @click="showForm = false">
          <span class="r-icon d-inline-flex align-items-center justify-content-center text-white fw-bold rounded-3">
            R
          </span>
          Receptkönyv
        </button>

        <div class="d-flex align-items-center gap-4">
          <button type="button" class="nav-link text-secondary fw-medium p-0 btn btn-link" @click="showForm = false">
            Receptek
          </button>

          <button class="btn btn-success text-white fw-medium px-3 py-2 rounded-3" @click="showForm = true">
            + Új recept
          </button>
        </div>
      </div>
    </nav>
  </header>

  <main class="container my-4">
    <UjRecept v-if="showForm" @addRecipe="addRecipe" />
    <Recept v-else :recipes="recipes" />
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
