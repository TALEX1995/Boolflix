<script>
import SearchBar from './SearchBar.vue'
import { store } from '../data/store'

export default {

    data() {
        return {
            store
        }
    },

    components: {
        SearchBar
    },

    emits: ['searched-film'],

    methods: {
        getMovieName(name) {
            this.$emit('searched-film', name)
        }
    }
}
</script>

<template>
    <SearchBar :labelInput="'Inserisci il titolo del film'" @form-submit="getMovieName" />
</template>

<style></style>