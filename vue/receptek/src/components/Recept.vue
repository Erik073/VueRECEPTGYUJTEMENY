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
    <section class="py-5 bg-light">
        <div class="container">
            <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-4">

                <div class="col">
                    <div class="card h-100 border-0 shadow-sm rounded-4 overflow-hidden recipe-card">
                        <div class="position-relative">
                            <img src="/src/assets/husleves.webp" class="card-img-top object-fit-cover"
                                style="height: 200px;" alt="Gulyásleves">
                            <span
                                class="badge bg-white text-dark rounded-pill position-absolute bottom-0 end-0 m-3 px-3 py-2 shadow-sm fw-semibold">🕒
                                50 perc</span>
                        </div>
                        <div class="card-body d-flex flex-column p-4">
                            <div class="mb-2"><span class="badge rounded-pill badge-easy px-3 py-1">Könnyű</span></div>
                            <h5 class="card-title fw-bold mb-2">Gulyásleves</h5>
                            <p class="card-text text-muted small mb-4">A magyar konyha egyik legismertebb levese,
                                marhahússal, zöldségekkel és fűszerpaprikával.</p>
                            <a href="#"
                                class="btn btn-recipe w-100 mt-auto py-2 px-3 rounded-3 d-flex justify-content-between align-items-center fw-semibold">
                                <span>Recept megtekintése</span><span>&rarr;</span>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="col">
                    <div class="card h-100 border-0 shadow-sm rounded-4 overflow-hidden recipe-card">
                        <div class="position-relative">
                            <img src="/src/assets/husleves.webp" class="card-img-top object-fit-cover"
                                style="height: 200px;" alt="Paprikás krumpli">
                            <span
                                class="badge bg-white text-dark rounded-pill position-absolute bottom-0 end-0 m-3 px-3 py-2 shadow-sm fw-semibold">🕒
                                60 perc</span>
                        </div>
                        <div class="card-body d-flex flex-column p-4">
                            <div class="mb-2"><span class="badge rounded-pill badge-medium px-3 py-1">Közepes</span>
                            </div>
                            <h5 class="card-title fw-bold mb-2">Paprikás krumpli</h5>
                            <p class="card-text text-muted small mb-4">Tartalmas egytálétel burgonyából, kolbásszal,
                                hagymával és fűszerpaprikával.</p>
                            <a href="#"
                                class="btn btn-recipe w-100 mt-auto py-2 px-3 rounded-3 d-flex justify-content-between align-items-center fw-semibold">
                                <span>Recept megtekintése</span><span>&rarr;</span>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="col">
                    <div class="card h-100 border-0 shadow-sm rounded-4 overflow-hidden recipe-card">
                        <div class="position-relative">
                            <img src="/src/assets/husleves.webp" class="card-img-top object-fit-cover"
                                style="height: 200px;" alt="Palacsinta">
                            <span
                                class="badge bg-white text-dark rounded-pill position-absolute bottom-0 end-0 m-3 px-3 py-2 shadow-sm fw-semibold">🕒
                                20 perc</span>
                        </div>
                        <div class="card-body d-flex flex-column p-4">
                            <div class="mb-2"><span class="badge rounded-pill badge-hard px-3 py-1">Nehéz</span></div>
                            <h5 class="card-title fw-bold mb-2">Palacsinta</h5>
                            <p class="card-text text-muted small mb-4">Vékony, könnyű tésztájú palacsinta, amely
                                lekvárral, kakaóval vagy túróval is megtölthető.</p>
                            <a href="#"
                                class="btn btn-recipe w-100 mt-auto py-2 px-3 rounded-3 d-flex justify-content-between align-items-center fw-semibold">
                                <span>Recept megtekintése</span><span>&rarr;</span>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="col">
                    <div class="card h-100 border-0 shadow-sm rounded-4 overflow-hidden recipe-card">
                        <div class="position-relative">
                            <img src="/src/assets/husleves.webp" class="card-img-top object-fit-cover"
                                style="height: 200px;" alt="Túrógombóc">
                            <span
                                class="badge bg-white text-dark rounded-pill position-absolute bottom-0 end-0 m-3 px-3 py-2 shadow-sm fw-semibold">🕒
                                20 perc</span>
                        </div>
                        <div class="card-body d-flex flex-column p-4">
                            <div class="mb-2"><span class="badge rounded-pill badge-easy px-3 py-1">Könnyű</span></div>
                            <h5 class="card-title fw-bold mb-2">Túrógombóc</h5>
                            <p class="card-text text-muted small mb-4">Puha túrógombóc pirított zsemlemorzsában,
                                tejföllel és porcukorral tálalva.</p>
                            <a href="#"
                                class="btn btn-recipe w-100 mt-auto py-2 px-3 rounded-3 d-flex justify-content-between align-items-center fw-semibold">
                                <span>Recept megtekintése</span><span>&rarr;</span>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="col">
                    <div class="card h-100 border-0 shadow-sm rounded-4 overflow-hidden recipe-card">
                        <div class="position-relative">
                            <img src="/src/assets/husleves.webp" class="card-img-top object-fit-cover"
                                style="height: 200px;" alt="Margherita pizza">
                            <span
                                class="badge bg-white text-dark rounded-pill position-absolute bottom-0 end-0 m-3 px-3 py-2 shadow-sm fw-semibold">🕒
                                45 perc</span>
                        </div>
                        <div class="card-body d-flex flex-column p-4">
                            <div class="mb-2"><span class="badge rounded-pill badge-medium px-3 py-1">Közepes</span>
                            </div>
                            <h5 class="card-title fw-bold mb-2">Margherita pizza</h5>
                            <p class="card-text text-muted small mb-4">Klasszikus olasz pizza paradicsomszósszal,
                                mozzarellával és friss bazsalikommal.</p>
                            <a href="#"
                                class="btn btn-recipe w-100 mt-auto py-2 px-3 rounded-3 d-flex justify-content-between align-items-center fw-semibold">
                                <span>Recept megtekintése</span><span>&rarr;</span>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="col">
                    <div class="card h-100 border-0 shadow-sm rounded-4 overflow-hidden recipe-card">
                        <div class="position-relative">
                            <img src="/src/assets/husleves.webp" class="card-img-top object-fit-cover"
                                style="height: 200px;" alt="Sajtos hamburger">
                            <span
                                class="badge bg-white text-dark rounded-pill position-absolute bottom-0 end-0 m-3 px-3 py-2 shadow-sm fw-semibold">🕒
                                25 perc</span>
                        </div>
                        <div class="card-body d-flex flex-column p-4">
                            <div class="mb-2"><span class="badge rounded-pill badge-medium px-3 py-1">Közepes</span>
                            </div>
                            <h5 class="card-title fw-bold mb-2">Sajtos hamburger</h5>
                            <p class="card-text text-muted small mb-4">Szaftos marhahúspogácsa olvadt sajttal, friss
                                zöldségekkel és puha buciban.</p>
                            <a href="#"
                                class="btn btn-recipe w-100 mt-auto py-2 px-3 rounded-3 d-flex justify-content-between align-items-center fw-semibold">
                                <span>Recept megtekintése</span><span>&rarr;</span>
                            </a>
                        </div>
                    </div>
                </div>
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

.btn-recipe {
    background-color: #2f855a;
    color: #ffffff;
    border: none;
    transition: background-color 0.2s ease, transform 0.2s ease;
}

.btn-recipe:hover {
    background-color: #276749;
    color: #ffffff;
}

.badge-easy {
    background-color: #2f855a;
    color: #ffffff;
}

.badge-medium {
    background-color: #ecc94b;
    color: #2d3748;
}

.badge-hard {
    background-color: #c53030;
    color: #ffffff;
}

.recipe-card {
    transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.recipe-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 .5rem 1rem rgba(0, 0, 0, .1) !important;
}
</style>
