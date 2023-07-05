<script>
import SearchBar from './SearchBar.vue'

export default {
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