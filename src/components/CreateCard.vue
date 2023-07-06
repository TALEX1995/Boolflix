<script>
export default {
    props: {
        item: Object,
    },

    computed: {
        hasFlag() {
            return this.item.originalLanguage === 'en' || this.item.originalLanguage === 'it'
        },

        getFlagSrc() {
            const url = new URL(`../assets/img/${this.item.originalLanguage}.png`, import.meta.url);

            return url.href
        }
    }
}
</script>

<template>
    <ul>
        <li>
            <img :src="item.posterUrl" :alt="item.originalTitle">
        </li>
        <li>Titolo originale: {{ item.originalTitle }}</li>
        <li>Titolo in Italiano: {{ item.itTitle }}</li>

        <!-- Condition to change language in a flag if they are en or it -->
        <li v-if="this.hasFlag">
            <img class="flag" :src="getFlagSrc" :alt="item.originalLanguage">
        </li>
        <li v-else>Lingua: {{ item.originalLanguage }}</li>
        <li>

            <!-- Cicle to change vote in star -->
            <span v-for="index in 5" :key="index">
                <span v-if="item.vote >= index"><font-awesome-icon :icon="['fas', 'star']" /></span>
                <span v-else> <font-awesome-icon :icon="['far', 'star']" /> </span>
            </span>

        </li>
    </ul>
</template>


<style scoped>
img.flag {
    max-width: 40px;
    height: auto;
}
</style>