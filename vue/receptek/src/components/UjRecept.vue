<script setup>
import { ref } from 'vue'

const emit = defineEmits(['addRecipe'])

const name = ref('')
const image = ref('')
const description = ref('')
const difficulty = ref('Könnyű')

function addRecipe() {
    emit('addRecipe', {
        name: name.value,
        image: image.value,
        description: description.value,
        difficulty: difficulty.value
    })

    name.value = ''
    image.value = ''
    description.value = ''
    difficulty.value = 'Könnyű'
}
</script>

<template>
    <header>
        <h1>ÚJ Recept</h1>
    </header>
    <main>
   <form @submit.prevent="addRecipe">

        <div class="mb-3">
            <label class="form-label">Recept neve</label>
            <input v-model="name" class="form-control" required>
        </div>

        <div class="mb-3">
            <label class="form-label">Kép URL</label>
            <input v-model="image" class="form-control">
        </div>

        <div class="mb-3">
            <label class="form-label">Leírás</label>
            <textarea v-model="description" class="form-control"></textarea>
        </div>

        <div class="mb-3">
            <label class="form-label">Nehézség</label>
            <select v-model="difficulty" class="form-select">
                <option>Könnyű</option>
                <option>Közepes</option>
                <option>Nehéz</option>
            </select>
        </div>

        <button class="btn btn-primary" type="submit">
            Recept hozzáadása
        </button>

    </form>
  </main>
  <footer>
    <p>Minden oké</p>
  </footer>
</template>

<style scoped>

</style>