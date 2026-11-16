<script setup>
defineProps({
    recipes: {
        type: Array,
        required: true
    }
})
</script>

<template>
    <div
        v-for="(recipe, index) in recipes"
        :key="index"
        class="col"
    >
        <div class="card h-100 border-0 shadow-sm rounded-4 overflow-hidden recipe-card">

            <div class="position-relative">
                <img
                    :src="recipe.image"
                    class="card-img-top object-fit-cover"
                    style="height: 200px;"
                    :alt="recipe.name"
                >

                <span class="badge bg-white text-dark rounded-pill position-absolute bottom-0 end-0 m-3 px-3 py-2 shadow-sm fw-semibold">
                    🕒 {{ recipe.time }} perc
                </span>
            </div>

            <div class="card-body d-flex flex-column p-4">

                <div class="mb-2">
                    <span
                        class="badge rounded-pill px-3 py-1"
                        :class="{
                            'badge-easy': recipe.difficulty === 'Könnyű',
                            'badge-medium': recipe.difficulty === 'Közepes',
                            'badge-hard': recipe.difficulty === 'Nehéz'
                        }"
                    >
                        {{ recipe.difficulty }}
                    </span>
                </div>

                <h5 class="card-title fw-bold mb-2">
                    {{ recipe.name }}
                </h5>

                <p class="card-text text-muted small mb-4">
                    {{ recipe.description }}
                </p>

                <a
                    href="#"
                    class="btn btn-recipe w-100 mt-auto py-2 px-3 rounded-3 d-flex justify-content-between align-items-center fw-semibold"
                >
                    <span>Recept megtekintése</span>
                    <span>&rarr;</span>
                </a>

            </div>
        </div>
    </div>
</template>