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

    emits: ['searched-term'],

    methods: {
        getTitleFilter(name) {
            this.$emit('searched-term', name)
        }
    }
}
</script>

<template>
    <SearchBar :labelInput="'Inserisci il titolo del film o della serie tv'" @form-submit="getTitleFilter" />
</template>

<style></style>