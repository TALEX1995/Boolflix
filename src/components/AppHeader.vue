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
    <font-awesome-icon :icon="['fas', 'star']" />
    <font-awesome-icon :icon="['far', 'star']" />
    <SearchBar :labelInput="'Inserisci il titolo del film o della serie tv'" @form-submit="getTitleFilter" />
</template>

<style></style>