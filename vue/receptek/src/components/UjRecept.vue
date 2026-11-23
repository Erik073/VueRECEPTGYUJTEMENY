<script setup>
import { reactive, watch } from 'vue'

const props = defineProps({
  recipe: {
    type: Object,
    default: null
  }
})

const emit = defineEmits(['addRecipe', 'updateRecipe'])

const defaultImage = new URL('../assets/husleves.webp', import.meta.url).href

const form = reactive({
  name: '',
  image: '',
  description: '',
  difficulty: 'Könnyű',
  time: 30
})

const errors = reactive({})

watch(() => props.recipe, (recipe) => {
  if (recipe) {
    form.name = recipe.name
    form.image = recipe.image
    form.description = recipe.description
    form.difficulty = recipe.difficulty
    form.time = recipe.time
  } else {
    resetForm()
  }
}, { immediate: true })

function validateForm() {
  errors.name = !form.name.trim() ? 'A recept neve kötelező.' : ''
  errors.description = !form.description.trim() ? 'A leírás megadása kötelező.' : ''
  errors.time = Number(form.time) <= 0 ? 'Az elkészítési időnek nagyobbnak kell lennie nullánál.' : ''
  errors.difficulty = !form.difficulty ? 'Válassz nehézségi szintet.' : ''

  return !Object.values(errors).some((value) => Boolean(value))
}

function handleImage(event) {
  const file = event.target.files?.[0]

  if (!file) return

  const reader = new FileReader()

  reader.onload = () => {
    form.image = reader.result
  }

  reader.readAsDataURL(file)
}

function resetForm() {
  form.name = ''
  form.image = ''
  form.description = ''
  form.difficulty = 'Könnyű'
  form.time = 30

  Object.keys(errors).forEach((key) => delete errors[key])
}

function saveRecipe() {
  if (!validateForm()) {
    return
  }

  const savedRecipe = {
    name: form.name.trim(),
    image: form.image || defaultImage,
    description: form.description.trim(),
    difficulty: form.difficulty,
    time: Number(form.time)
  }

  if (props.recipe) {
    emit('updateRecipe', {
      ...savedRecipe,
      id: props.recipe.id
    })
  } else {
    emit('addRecipe', savedRecipe)
  }

  resetForm()
}
</script>

<template>
  <header>
    <h1>{{ props.recipe ? 'Recept módosítása' : 'Új recept' }}</h1>
  </header>

  <main>
    <form @submit.prevent="saveRecipe" class="row g-3">
      <div class="col-12">
        <label class="form-label">Recept neve</label>
        <input v-model="form.name" type="text" class="form-control" required>
        <small v-if="errors.name" class="text-danger d-block mt-1">{{ errors.name }}</small>
      </div>

      <div class="col-12">
        <label class="form-label">Recept képe</label>
        <input type="file" class="form-control" accept="image/*" @change="handleImage">
      </div>

      <div class="col-12">
        <label class="form-label">Leírás</label>
        <textarea v-model="form.description" class="form-control" rows="4"></textarea>
        <small v-if="errors.description" class="text-danger d-block mt-1">{{ errors.description }}</small>
      </div>

      <div class="col-md-6">
        <label class="form-label">Nehézség</label>
        <select v-model="form.difficulty" class="form-select">
          <option value="Könnyű">Könnyű</option>
          <option value="Közepes">Közepes</option>
          <option value="Nehéz">Nehéz</option>
        </select>
        <small v-if="errors.difficulty" class="text-danger d-block mt-1">{{ errors.difficulty }}</small>
      </div>

      <div class="col-md-6">
        <label class="form-label">Elkészítési idő (perc)</label>
        <input v-model="form.time" type="number" min="1" class="form-control" required>
        <small v-if="errors.time" class="text-danger d-block mt-1">{{ errors.time }}</small>
      </div>

      <div class="col-12">
        <button class="btn btn-success" type="submit">
          {{ props.recipe ? 'Recept módosítása' : 'Recept hozzáadása' }}
        </button>
      </div>
    </form>
  </main>
</template>
