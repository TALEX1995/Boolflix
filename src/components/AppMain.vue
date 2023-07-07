<script>
import CreateCard from './CreateCard.vue'
import { store } from '../data/store'
export default {
    data() {
        return {
            store
        }
    },

    components: {
        CreateCard
    }
}
</script>

<template>
    <main class="container">
        <!-- Movie -->
        <h2>Movie</h2>
        <section class="row row-cols-3">

            <CreateCard v-for="movie in store.filteredMovies" :item="movie" :key="movie" />

        </section>

        <!-- Series -->
        <h2>Series</h2>
        <section class="row row-cols-3">

            <CreateCard v-for="serie in store.filteredSeries" :item="serie" :key="serie" />

        </section>
    </main>
</template>


<style lang="scss" scoped>
@use '../assets/scss/vars' as *;

main {
    background-color: $main-bkg;
}

h2 {
    color: $white;
    font-size: $rem3;
    text-align: center;
    padding: $rem150 0;
}
</style>