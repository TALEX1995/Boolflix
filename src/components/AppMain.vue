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
    },

    computed: {
        hasProduct() {
            return store.filteredMovies.length || store.filteredSeries.length ? true : false
        }
    }
}
</script>

<template>
    <main class="container d-flex justify-content-center align-items-center" v-if="!hasProduct">
        <h3>Inserisci un titolo di un film o una serie TV nella barra di ricerca</h3>
    </main>
    <main v-else class="container">
        <!-- Movie -->
        <h2>Movie</h2>
        <section id="movie" class="row row-cols-1 row-cols-md-2 row-cols-lg-4">

            <CreateCard v-for="movie in store.filteredMovies" :item="movie" :key="movie" />

        </section>

        <!-- Series -->
        <h2>Series</h2>
        <section id="series" class="row row-cols-1 row-cols-md-2 row-cols-lg-4">

            <CreateCard v-for="serie in store.filteredSeries" :item="serie" :key="serie" />

        </section>
    </main>
</template>


<style lang="scss" scoped>
@use '../assets/scss/vars' as *;

main {
    background-color: $main-bkg;
    height: calc(100vh - 100px);
    overflow: auto;
}

h2 {
    color: $white;
    font-size: $rem3;
    text-align: center;
    padding: $rem150 0;
}

#movie {
    border-bottom: 2px solid white;
}
</style>