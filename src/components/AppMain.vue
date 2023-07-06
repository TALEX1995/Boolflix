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
    <CreateCard :listItem="store.filteredMovie" />
    <CreateCard :listItem="store.filteredSeries" />
</template>


<style></style>