<script setup>
import { ref } from 'vue'

const emit = defineEmits(['addRecipe'])

const name = ref('')
const image = ref('')
const description = ref('')
const difficulty = ref('Könnyű')
const time = ref('')

function handleImage(event) {
    const file = event.target.files[0]

    if (file) {
        image.value = URL.createObjectURL(file)
    }
}

function addRecipe() {
    emit('addRecipe', {
        name: name.value,
        image: image.value,
        description: description.value,
        difficulty: difficulty.value,
        time: time.value
    })

    name.value = ''
    image.value = ''
    description.value = ''
    difficulty.value = 'Könnyű'
    time.value = ''
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
                <input
                    type="text"
                    v-model="name"
                    class="form-control"
                    required
                >
            </div>

            <div class="mb-3">
                <label class="form-label">Recept képe</label>
                <input
                    type="file"
                    class="form-control"
                    accept="image/*"
                    @change="handleImage"
                    required
                >
            </div>

            <div class="mb-3">
                <label class="form-label">Leírás</label>
                <textarea
                    type="text"
                    v-model="description"
                    class="form-control"
                ></textarea>
            </div>

            <div class="mb-3">
                <label class="form-label">Nehézség</label>
                <select
                    v-model="difficulty"
                    class="form-select"
                >
                    <option>Könnyű</option>
                    <option>Közepes</option>
                    <option>Nehéz</option>
                </select>
            </div>

                 <div class="mb-3">
                <label class="form-label">Elkészítési idő</label>
                <input
                    type="number"
                    v-model="time"
                    class="form-control"
                    required
                >
            </div>

            <button class="btn btn-success" type="submit">
                Recept hozzáadása
            </button>

        </form>
    </main>
</template>

<style scoped>

</style>