<script>
import axios from 'axios';
import { store } from './data/store';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
const keyApi = '560d97e59a83a4717fcd53ac0254fd86';
const baseUri = 'https://api.themoviedb.org/3/search';

export default {

    data() {
        return {

        }
    },

    components: {
        AppHeader,
        AppMain
    },

    methods: {
        filteredMovie(name) {
            axios.get(`${baseUri}/movie?api_key=${keyApi}&query=${name}&language=it-IT`)
                .then((res) => {
                    store.filteredMovies = res.data.results.map((movie) => {
                        const { original_title, original_language, title, vote_average } = movie
                        const vote = Math.ceil(vote_average / 2)
                        return { originalTitle: original_title, originalLanguage: original_language, itTitle: title, vote }
                    })
                }).catch((err) => {
                    console.log(err)
                })
        },

        filteredSeries(name) {
            axios.get(`${baseUri}/tv?api_key=${keyApi}&query=${name}&language=it-IT`)
                .then((res) => {
                    store.filteredSeries = res.data.results.map((movie) => {
                        const { original_name, original_language, name, vote_average } = movie
                        const vote = Math.ceil(vote_average / 2)
                        return { originalTitle: original_name, originalLanguage: original_language, itTitle: name, vote }
                    })
                }).catch((err) => {
                    console.log(err)
                })
        },

        filterMovieAndSeries(name) {
            if (!name) {
                store.filteredMovies = [];
                store.filteredSeries = [];
                return;
            }
            this.filteredMovie(name)
            this.filteredSeries(name)
        }
    }
}
</script>

<template>
    <AppHeader @searched-term="filterMovieAndSeries" />
    <AppMain />
</template>


<style></style>