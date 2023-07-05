<script>
import axios from 'axios';
import { store } from './data/store';
import AppHeader from './components/AppHeader.vue';
const keyApi = '560d97e59a83a4717fcd53ac0254fd86';
const baseUri = 'https://api.themoviedb.org/3/search';

export default {

    data() {
        return {
            store
        }
    },

    components: {
        AppHeader,
    },

    methods: {
        filteredMovie(name) {
            axios.get(`${baseUri}/movie?api_key=${keyApi}&query=${name}&language=it-IT`)
                .then((res) => {
                    store.filteredMovie = res.data.results.map((movie) => {
                        const { original_title, original_language, title, vote_average } = movie
                        const vote = Math.ceil(vote_average / 2)
                        return { originalTitle: original_title, originalLanguage: original_language, itTitle: title, vote }
                    })
                }).catch((err) => {
                    console.log(err)
                })
        }
    }
}
</script>

<template>
    <AppHeader @searched-film="filteredMovie" />
</template>


<style></style>