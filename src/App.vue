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
        // Api request movie title based on user input text
        filteredMovie(name) {
            axios.get(`${baseUri}/movie?api_key=${keyApi}&query=${name}&language=it-IT`)
                .then((res) => {
                    store.filteredMovies = res.data.results.map((movie) => {
                        const { original_title, original_language, title, vote_average, poster_path } = movie
                        const vote = Math.ceil(vote_average / 2)
                        const posterUrl = `https://image.tmdb.org/t/p/w342/${poster_path}`
                        return { originalTitle: original_title, originalLanguage: original_language, itTitle: title, vote, posterUrl }
                    })
                }).catch((err) => {
                    console.log(err)
                })
        },

        // Api request series title based on user input text
        filteredSeries(name) {
            axios.get(`${baseUri}/tv?api_key=${keyApi}&query=${name}&language=it-IT`)
                .then((res) => {
                    store.filteredSeries = res.data.results.map((movie) => {
                        const { original_name, original_language, name, vote_average, poster_path } = movie
                        const vote = Math.ceil(vote_average / 2)
                        const posterUrl = `https://image.tmdb.org/t/p/w342/${poster_path}`
                        return { originalTitle: original_name, originalLanguage: original_language, itTitle: name, vote, posterUrl }
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


<style lang="scss">
@use './assets/scss/style.scss'
</style>