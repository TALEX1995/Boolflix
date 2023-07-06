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
    <!-- Movie -->
    <div>
        <h2>Movie</h2>
        <CreateCard v-for="movie in store.filteredMovies" :item="movie" :key="movie" />
    </div>
    <!-- Series -->
    <div>
        <h2>Series</h2>
        <CreateCard v-for="serie in store.filteredSeries" :item="serie" :key="serie" />
    </div>
</template>


<style></style>