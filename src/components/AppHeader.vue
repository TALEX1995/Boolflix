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
    <header class="container">
        <img src="../assets/img/logoBoolflix.png" alt="Boolflix">
        <SearchBar :placeholder="'Cerca il titolo di un film o serie tv'" @form-submit="getTitleFilter" />
    </header>
</template>

<style lang="scss" scoped>
@use '../assets/scss/_vars.scss' as *;

header {
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100px;
    background-color: $header-bkg;
}
</style>