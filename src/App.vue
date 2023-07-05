<script>
import AppHeader from './components/AppHeader.vue'
const keyApi = '560d97e59a83a4717fcd53ac0254fd86'

export default {
    components: {
        AppHeader,
    },

    methods: {
        filteredFilm(name) {
            console.log(name)
        }
    }
}
</script>

<template>
    <AppHeader @searched-film="filteredFilm" />
</template>


<style></style>