<script setup>
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
                        <input type="text" class="form-control form-control-lg rounded-3 border-secondary-subtle fs-6"
                            placeholder="Keress receptet..." aria-label="Keress receptet">
                    </div>
                    <div class="col-12 col-md-3">
                        <select class="form-select form-select-lg rounded-3 border-secondary-subtle fs-6"
                            aria-label="Nehézségi szint">
                            <option selected value="">Minden nehézség</option>
                            <option value="konnyu">Könnyű</option>
                            <option value="kozepes">Közepes</option>
                            <option value="nehez">Nehéz</option>
                        </select>
                    </div>
                    <div class="col-12 col-md-3">
                        <select class="form-select form-select-lg rounded-3 border-secondary-subtle fs-6"
                            aria-label="Elkészítési idő">
                            <option selected value="">Elkészítési idő szerint</option>
                            <option value="15">15 perc alatt</option>
                            <option value="30">30 perc alatt</option>
                            <option value="60">60 perc alatt</option>
                        </select>
                    </div>

                </div>
            </form>
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
