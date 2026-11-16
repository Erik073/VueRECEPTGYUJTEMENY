<script setup>
import { computed, ref } from 'vue'
import Kartyak from './Kartya.vue'

const props = defineProps({
    recipes: {
        type: Array,
        required: true
    }
})

const searchTerm = ref('')
const selectedDifficulty = ref('')
const sortBy = ref('name')

const filteredRecipes = computed(() => {
    const term = searchTerm.value.trim().toLowerCase()

    return props.recipes.filter((recipe) => {
        const matchesSearch = !term ||
            (recipe.name && recipe.name.toLowerCase().includes(term)) ||
            (recipe.description && recipe.description.toLowerCase().includes(term))

        const matchesDifficulty = !selectedDifficulty.value || recipe.difficulty === selectedDifficulty.value

        return matchesSearch && matchesDifficulty
    })
})

const sortedRecipes = computed(() => {
    const recipesCopy = [...filteredRecipes.value]

    switch (sortBy.value) {
        case 'time-asc':
            return recipesCopy.sort((a, b) => Number(a.time || 0) - Number(b.time || 0))
        case 'time-desc':
            return recipesCopy.sort((a, b) => Number(b.time || 0) - Number(a.time || 0))
        case 'difficulty':
            return recipesCopy.sort((a, b) => {
                const difficultyOrder = { 'Könnyű': 1, 'Közepes': 2, 'Nehéz': 3 }
                return (difficultyOrder[a.difficulty] || 0) - (difficultyOrder[b.difficulty] || 0)
            })
        case 'name':
        default:
            return recipesCopy.sort((a, b) => (a.name || '').localeCompare(b.name || ''))
    }
})
</script>

<template>
    <section>
        <p class="rcptgyjtmny">receptgyűjtemény</p>
        <h2>Mit főzzünk ma?</h2>
    </section>

    <section>
        <div class="container my-4">
            <form class="p-3 bg-white rounded-4 shadow-sm border border-light">
                <div class="row g-3 align-items-center">
                    <div class="col-12 col-md-6">
                        <input v-model="searchTerm" type="text"
                            class="form-control form-control-lg rounded-3 border-secondary-subtle fs-6"
                            placeholder="Keress receptet..." aria-label="Keress receptet">
                    </div>

                    <div class="col-12 col-md-3">
                        <select v-model="selectedDifficulty"
                            class="form-select form-select-lg rounded-3 border-secondary-subtle fs-6"
                            aria-label="Nehézségi szint">
                            <option value="">Minden nehézség</option>
                            <option value="Könnyű">Könnyű</option>
                            <option value="Közepes">Közepes</option>
                            <option value="Nehéz">Nehéz</option>
                        </select>
                    </div>

                    <div class="col-12 col-md-3">
                        <select v-model="sortBy"
                            class="form-select form-select-lg rounded-3 border-secondary-subtle fs-6"
                            aria-label="Rendezés">
                            <option value="name">Név szerint</option>
                            <option value="difficulty">Nehézség szerint</option>
                            <option value="time-asc">Idő szerint ↑</option>
                            <option value="time-desc">Idő szerint ↓</option>
                        </select>
                    </div>
                </div>
            </form>
        </div>
    </section>

    <section class="py-5 bg-light">
        <div class="container">
            <div v-if="sortedRecipes.length === 0" class="alert alert-info mb-0">
                Nincs találat a kiválasztott szűréshez.
            </div>

            <div v-else class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-4">
                <Kartyak v-for="(recipe, index) in sortedRecipes" :key="recipe.id ?? index" :recipe="recipe" />
            </div>
        </div>
    </section>
</template>

<style scoped>
h2 {
    font-weight: bolder;
}

.rcptgyjtmny {
    color: #3d7a5b;
    font-variant: small-caps;
    font-weight: 900;
}
</style>
